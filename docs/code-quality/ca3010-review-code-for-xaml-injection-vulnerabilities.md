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
ms.openlocfilehash: efd30a783f534d76f7f7f3fa18fd181dbe7e98a1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237238"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)

|||
|-|-|
|TypeName|Reviewcodeforxamlinjectionsicherheitssicherheitsanfälligkeiten|
|CheckId|CA3010|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderungs Eingaben <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> erreichen eine Load-Methode.

## <a name="rule-description"></a>Regelbeschreibung

Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben XAML Injection-Angriffe. XAML ist eine Markupsprache, die Objektinstanziierung und -ausführung direkt darstellt. Dies bedeutet, dass in XAML erstellte Elemente mit Systemressourcen interagieren können (z. b. Netzwerk Zugriff und Dateisystem-e/a). Wenn ein Angreifer die Eingabe für einen <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> Lade Methodenaufrufe steuern kann, kann der Angreifer Code ausführen.

Diese Regel versucht, Eingaben von HTTP-Anforderungen zu suchen, <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> die eine Load-Methode erreichen.

> [!NOTE]
> Diese Regel kann keine Daten über Assemblys hinweg verfolgen. Wenn eine Assembly z. b. die HTTP-Anforderungs Eingabe liest und Sie dann an eine andere Assembly übergibt, die XAML lädt, erzeugt diese Regel keine Warnung.

> [!NOTE]
> Es gibt eine konfigurierbare Beschränkung, wie tief diese Regel den Datenfluss über Methodenaufrufe hinweg analysieren wird. Weitere Informationen zum Konfigurieren des Limits in einer Editor config-Datei finden Sie unter [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Nicht vertrauenswürdiges XAML laden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Warnungen von dieser Regel nicht unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

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
