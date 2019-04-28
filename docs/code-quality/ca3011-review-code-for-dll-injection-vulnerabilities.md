---
title: 'CA3011: Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)'
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
ms.openlocfilehash: a6f3a2db89e35408a19cec47c971821fedf5f85a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541141"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderung, dass die Eingabe einer Methode, die erreicht hat, lädt eine Assembly.

## <a name="rule-description"></a>Regelbeschreibung

Bei der Arbeit mit nicht vertrauenswürdigen Eingaben Achten Sie darauf, dass Sie beim Laden von nicht vertrauenswürdigem Code. Wenn Ihre Webanwendung nicht vertrauenswürdigen Code geladen wird, ist ein Angreifer möglicherweise böswilligen DLLs in den Prozess einfügen und schädlichen Code ausführen können.

Mit dieser Regel versucht, die Eingabe aus einer HTTP-Anforderung zu finden, die eine Methode erreicht wird, die eine Assembly geladen.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die eine Assembly lädt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Nicht vertrauenswürdige DLLs nicht aus Benutzereingaben geladen werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Nicht unterdrücken von Warnungen, die von dieser Regel.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
