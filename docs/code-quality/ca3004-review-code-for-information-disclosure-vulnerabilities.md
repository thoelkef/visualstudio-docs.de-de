---
title: 'CA3004: Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)'
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
ms.openlocfilehash: 8e8c8c58a01b9527df472907c8b55a9d175dd91d
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841605"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Meldung, stapelüberwachung oder eine Zeichenfolgendarstellung einer Ausnahme erreicht Webausgabe.

## <a name="rule-description"></a>Regelbeschreibung

Veröffentlichung von Ausnahmeinformationen erhalten Angreifer, die einen Einblick in die Interna von Ihrer Anwendung, die Angreifer kann finden Sie weitere Sicherheitsrisiken, die ausgenutzt.

Mit dieser Regel versucht, eine Ausnahmemeldung, die stapelüberwachung und die Zeichenfolgendarstellung, die die Ausgabe in eine HTTP-Antwort zu finden.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly wird eine Ausnahme abgefangen und leitet diese dann an eine andere Assembly, die die Ausnahme ausgibt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) für den Grenzwert in einer EditorConfig-Datei zu konfigurieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Ausgegeben Sie Informationen zur Ausnahme zu HTTP-Antworten nicht werden. Stattdessen geben Sie eine allgemeine Fehlermeldung. Finden Sie unter [OWASP Fehlerbehandlung Seite](https://www.owasp.org/index.php/Error_Handling) Weitere Anleitungen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie kennen Ihre Webausgabe innerhalb Ihrer Anwendung Vertrauensgrenze und niemals außerhalb verfügbar, es ist in Ordnung, diese Warnung unterdrücken. Dies kommt selten vor. Berücksichtigen Sie, die Ihrer Anwendung Vertrauensgrenze und Datenflüsse im Laufe der Zeit ändern können.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Lösung

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```