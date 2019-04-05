---
title: 'CA3002: Code für XSS-Anfälligkeiten überprüfen'
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
ms.openlocfilehash: a10f72297746a1e7bda3c69f8f7daf0efacd20bc
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018563"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Code für XSS-Anfälligkeiten überprüfen

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht unformatierten HTML-Ausgabe.

## <a name="rule-description"></a>Regelbeschreibung

Bei der Arbeit mit nicht vertrauenswürdigen Eingaben aus webanforderungen Achten Sie darauf, dass Sie von Cross-Site scripting (XSS)-Angriffe. XSS-Angriff fügt nicht vertrauenswürdige Eingaben in unformatierten HTML-Ausgabe, denen der Angreifer schädliche Skripts ausführen oder in böswilliger Absicht Ändern des Inhalts auf Ihrer Webseite. Ein übliches Verfahren wäre `<script>` Elemente mit bösartigem Code in der Eingabe. Weitere Informationen finden Sie unter [OWASP XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Mit dieser Regel versucht, Eingaben von HTTP-Anforderungen, die unformatierten HTML-Ausgabe erreichen zu finden.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die unformatiertes HTML ausgibt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Anstelle der Ausgabe von unformatierten HTML, verwenden Sie eine Methode oder Eigenschaft, erste HTML-Codierung der Eingabe.
- HTML-codieren nicht vertrauenswürdiger Daten vor dem Ausgeben von unformatierten HTML.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, falls:
- Sie wissen, dass die Eingabe mit einer bekannten, sicheren Reihe von Zeichen, die nicht mit HTML-Code überprüft wird.
- Sie wissen, dass die Daten in einer Weise, die nicht von dieser Regel erkannte HTML-codiert ist.

> [!NOTE]
> Diese Regel meldet möglicherweise falsch positive Ergebnisse für einige Methoden oder Eigenschaften, HTML-Codierung der Eingabe.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Lösung

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```