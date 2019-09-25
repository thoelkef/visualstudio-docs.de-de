---
title: 'CA3008: Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)'
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
ms.openlocfilehash: 1d001dc306bbb225c4ecc1c0f17bf46619e2d0a7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237259"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)

|||
|-|-|
|TypeName|Reviewcodeforxpthinjectionsicherheitsanfälligkeiten|
|CheckId|CA3008|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderungs Eingaben erreichen eine XPath-Abfrage.

## <a name="rule-description"></a>Regelbeschreibung

Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben die XPath-Injection-Angriffe. Das Erstellen von XPath-Abfragen mithilfe nicht vertrauenswürdiger Eingaben kann es einem Angreifer ermöglichen, die Abfrage bösartig zu manipulieren, um ein unbeabsichtigtes Ergebnis zurückzugeben, und möglicherweise den Inhalt der abgefragten XML-Daten offenzulegen.

Diese Regel versucht, Eingaben von HTTP-Anforderungen zu suchen, die einen XPath-Ausdruck erreichen.

> [!NOTE]
> Diese Regel kann keine Daten über Assemblys hinweg verfolgen. Wenn eine Assembly z. b. die HTTP-Anforderungs Eingabe liest und Sie dann an eine andere Assembly übergibt, die eine XPath-Abfrage ausführt, erzeugt diese Regel keine Warnung.

> [!NOTE]
> Es gibt eine konfigurierbare Beschränkung, wie tief diese Regel den Datenfluss über Methodenaufrufe hinweg analysieren wird. Weitere Informationen zum Konfigurieren des Limits in einer Editor config-Datei finden Sie unter [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Einige Ansätze zum Beheben von XPath-Injection-Sicherheitsrisiken sind:

- Erstellen Sie keine XPath-Abfragen aus der Benutzereingabe.
- Überprüfen Sie, ob die Eingabe nur einen sicheren Satz von Zeichen enthält.
- Escapezeichen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Wenn Sie wissen, dass Sie die Eingabe als sicher überprüft haben, ist es in Ordnung, diese Warnung zu unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

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
