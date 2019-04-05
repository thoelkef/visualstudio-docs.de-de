---
title: 'CA3008: Code nach XPath-Injection-Anfälligkeiten überprüfen'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018514"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Code nach XPath-Injection-Anfälligkeiten überprüfen

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht eine XPath-Abfrage.

## <a name="rule-description"></a>Regelbeschreibung

Achten Sie darauf von XPath-Injection-Angriffen, bei der Arbeit mit nicht vertrauenswürdigen Eingaben. Erstellen von XPath-Abfragen mit nicht vertrauenswürdigen Eingaben kann es Angreifern ermöglichen, die Abfrage, um eine unbeabsichtigte Ergebnissatz in böswilliger Absicht zu bearbeiten, und legen Sie den Inhalt des abgefragten XML-möglicherweise offen. 

Mit dieser Regel versucht, beim Suchen der Eingabespalte aus HTTP-Anforderungen, die einen XPath-Ausdruck erreicht.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die eine XPath-Abfrage ausführt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Einige Ansätze für die Behebung von XPath-Injection-Anfälligkeiten gehören:

- Erstellen Sie keine XPath-Abfragen aus der Benutzereingabe.
- Überprüfen Sie, dass die Eingabe nur eine sichere Gruppe von Zeichen enthält.
- Versehen Sie Anführungszeichen mit Escapezeichen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie, dass Sie die Eingabe zur Sicherheit überprüft haben wissen, kann ich diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")
        
        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
