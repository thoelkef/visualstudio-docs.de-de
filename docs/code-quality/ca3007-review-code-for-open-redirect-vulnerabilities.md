---
title: 'CA3007: Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)'
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
ms.openlocfilehash: dbafb6c05a3dba72d1614d6a955e20030a50c6ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541167"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht eine HTTP-Antwort-Umleitung.

## <a name="rule-description"></a>Regelbeschreibung

Bei der Arbeit mit nicht vertrauenswürdigen Eingaben Achten Sie darauf, dass Sie offene umleitungen Sicherheitsrisiken. Ein Angreifer kann ein Sicherheitsrisiko, das offene umleitungen um Ihre Website zu verwenden, geben Sie die Darstellung einer legitimen URL, aber einen ahnungslosen Besucher einer Phishing oder andere bösartige Website umleiten ausnutzen.

Mit dieser Regel versucht beim Suchen der Eingabespalte aus HTTP-Anforderungen, die eine HTTP-umleitungs-URL zu erreichen.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die mit einer HTTP-Umleitung antwortet, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Einige Ansätze für die Behebung von Sicherheitsrisiken für offene umleitungen sind:

- Ermöglichen Sie keine Benutzern das Einleiten von umleitungen.
- Dürfen Sie Benutzer geben Sie einen beliebigen Teil der URL in einem Szenario mit Umleitung nicht.
- Leitet zu einer vordefinierten"Liste" URLs zu beschränken.
- Überprüfen Sie umleitungs-URLs.
- Falls zutreffend, sollten Sie eine Haftungsausschluss-Seite verwenden, wenn Benutzer außerhalb Ihrer Website weitergeleitet werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie, dass Sie die Eingabe wissen, um die gewünschten URLs eingeschränkt werden, überprüft haben, kann ich diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
