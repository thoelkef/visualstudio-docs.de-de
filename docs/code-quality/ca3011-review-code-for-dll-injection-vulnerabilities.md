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
ms.openlocfilehash: a459be8c8ab028581c850f5b5770a95cb70e3510
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237193"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)

|||
|-|-|
|TypeName|Reviewcodefordllinjectionsicherheitsanfälligkeiten|
|CheckId|CA3011|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderungs Eingaben erreichen eine Methode, die eine Assembly lädt.

## <a name="rule-description"></a>Regelbeschreibung

Wenn Sie mit nicht vertrauenswürdigen Eingaben arbeiten, achten Sie darauf, nicht vertrauenswürdigen Code zu laden. Wenn Ihre Webanwendung nicht vertrauenswürdigen Code lädt, kann ein Angreifer möglicherweise böswillige DLLs in Ihren Prozess einfügen und bösartigen Code ausführen.

Diese Regel versucht, Eingaben aus einer HTTP-Anforderung zu suchen, die eine Methode erreicht, die eine Assembly lädt.

> [!NOTE]
> Diese Regel kann keine Daten über Assemblys hinweg verfolgen. Wenn eine Assembly z. b. die HTTP-Anforderungs Eingabe liest und Sie dann an eine andere Assembly übergibt, die eine Assembly lädt, erzeugt diese Regel keine Warnung.

> [!NOTE]
> Es gibt eine konfigurierbare Beschränkung, wie tief diese Regel den Datenfluss über Methodenaufrufe hinweg analysieren wird. Weitere Informationen zum Konfigurieren des Limits in einer Editor config-Datei finden Sie unter [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Nicht vertrauenswürdige DLLs aus Benutzereingaben nicht laden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Warnungen von dieser Regel nicht unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

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
