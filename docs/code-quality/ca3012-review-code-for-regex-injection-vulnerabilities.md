---
title: 'CA3012: Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)'
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
ms.openlocfilehash: 42808b3961b18a23f594800f9d0782c908c9b1ba
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237177"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)

|||
|-|-|
|TypeName|Reviewcodeforregexinjectionsicherheitsanfälligkeiten|
|CheckId|CA3012|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderungs Eingaben erreichen einen regulären Ausdruck.

## <a name="rule-description"></a>Regelbeschreibung

Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben die Regex Injection-Angriffe. Ein Angreifer kann eine Regex-Injektion verwenden, um einen regulären Ausdruck in böswilliger Weise zu ändern, damit der Regex unbeabsichtigte Ergebnisse findet oder der Regex übermäßige CPU beansprucht, was zu einem Denial-of-Service-Angriff führt.

Diese Regel versucht, Eingaben von HTTP-Anforderungen zu suchen, die einen regulären Ausdruck erreichen.

> [!NOTE]
> Diese Regel kann keine Daten über Assemblys hinweg verfolgen. Wenn eine Assembly z. b. die HTTP-Anforderungs Eingabe liest und Sie dann an eine andere Assembly übergibt, die einen regulären Ausdruck erstellt, generiert diese Regel keine Warnung.

> [!NOTE]
> Es gibt eine konfigurierbare Beschränkung, wie tief diese Regel den Datenfluss über Methodenaufrufe hinweg analysieren wird. Weitere Informationen zum Konfigurieren des Limits in einer Editor config-Datei finden Sie unter [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Zu den entschärfungen bei Regex-Injektionen gehören:

- Verwenden Sie bei der Verwendung regulärer Ausdrücke immer ein Übereinstimmungs [Timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) .
- Vermeiden Sie die Verwendung regulärer Ausdrücke auf der Grundlage von Benutzereingaben.
- Escapezeichen für Sonderzeichen aus Benutzer <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> Eingaben durch Aufrufen von oder einer anderen Methode.
- Nur nicht-Sonderzeichen von Benutzereingaben zulassen

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Wenn Sie wissen, dass Sie ein Übereinstimmungs [Timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) verwenden und die Benutzereingabe keine Sonderzeichen enthält, ist es in Ordnung, diese Warnung zu unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
