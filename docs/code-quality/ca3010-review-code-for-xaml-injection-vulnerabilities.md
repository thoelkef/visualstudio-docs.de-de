---
title: 'CA3010: Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)'
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
ms.openlocfilehash: ea53f5e0cddf1dc6c6caf4c7fcfb79af52ce354e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103692"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

HTTP-Anforderung, die potenziell nicht vertrauenswürdige Eingabe erreicht eine <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> Load-Methode.

## <a name="rule-description"></a>Regelbeschreibung

Achten Sie darauf von XAML-Injection-Angriffen, bei der Arbeit mit nicht vertrauenswürdigen Eingaben. XAML ist eine Markupsprache, die Objektinstanziierung und -ausführung direkt darstellt. Das bedeutet, dass die Systemressourcen (z. B. Netzwerk Zugriff und Dateisystem e/a) in XAML erstellte Elemente interagieren können. Wenn ein Angreifer, die Eingabe für steuern kann eine <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> -Methodenaufruf, laden, und klicken Sie dann die Angreifer den Code ausführen kann.

Mit dieser Regel versucht wird, um Eingaben von HTTP-Anforderungen zu suchen, die erreicht eine <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> Load-Methode.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die XAML geladen, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Geladen Sie nicht vertrauenswürdige XAML nicht werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Nicht unterdrücken von Warnungen, die von dieser Regel.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
