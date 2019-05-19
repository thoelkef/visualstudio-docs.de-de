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
ms.openlocfilehash: b66e28804e85b04b1492a20828c42a9b5efd3cf8
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841038"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht ein regulären Ausdrucks.

## <a name="rule-description"></a>Regelbeschreibung

Achten Sie darauf von Regex-Injection-Angriffen, bei der Arbeit mit nicht vertrauenswürdigen Eingaben. Ein Angreifer kann die Regex-Injection verwenden, um einen regulären Ausdruck, um dem regulären Ausdruck entsprechen unbeabsichtigte Ergebnisse zu gestalten oder zu dem regulären Ausdruck, der einen hohen CPU, was zu einem Denial-of-Service-Angriff zu nutzen in böswilliger Absicht zu ändern.

Mit dieser Regel versucht beim Suchen der Eingabespalte aus HTTP-Anforderungen, die einen regulären Ausdruck zu erreichen.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die einen regulären Ausdruck erstellt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) für den Grenzwert in einer EditorConfig-Datei zu konfigurieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Einige risikominderungen für Regex-einfügungen sind:

- Verwenden Sie immer eine [entsprechen Timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) bei Verwendung von regulären Ausdrücken.
- Vermeiden Sie mithilfe von regulären Ausdrücken, die auf Grundlage der Benutzereingabe.
- Escapesonderzeichen aus Benutzereingaben durch Aufrufen von <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> oder eine andere Methode.
- Können Sie nur nicht-Sonderzeichen aus Benutzereingaben.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie wissen, verwenden Sie eine [entsprechen Timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) und die Benutzereingabe wird keine Sonderzeichen enthalten, es ist in Ordnung ist, können Sie diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

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
