---
title: 'CA3006: Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)'
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
ms.openlocfilehash: 986607d7f42f49c99396bbb021c48bad549930c9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237281"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)

|||
|-|-|
|TypeName|Reviewcodeforprocesscommandinjectionsicherheitsanfälligkeiten|
|CheckId|CA3006|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige HTTP-Anforderungs Eingaben erreichen einen Verarbeitungs Befehl.

## <a name="rule-description"></a>Regelbeschreibung

Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben, dass Befehls Injection-Angriffe berücksichtigt werden. Ein Befehl zum Einschleusen von Befehlen kann bösartige Befehle auf dem zugrunde liegenden Betriebssystem ausführen und so die Sicherheit und Integrität des Servers beeinträchtigen.

Diese Regel versucht, Eingaben von HTTP-Anforderungen zu suchen, die einen Verarbeitungs Befehl erreichen.

> [!NOTE]
> Diese Regel kann keine Daten über Assemblys hinweg verfolgen. Wenn eine Assembly z. b. die HTTP-Anforderungs Eingabe liest und Sie dann an eine andere Assembly übergibt, die einen Prozess startet, erzeugt diese Regel keine Warnung.

> [!NOTE]
> Es gibt eine konfigurierbare Beschränkung, wie tief diese Regel den Datenfluss über Methodenaufrufe hinweg analysieren wird. Weitere Informationen zum Konfigurieren des Limits in einer Editor config-Datei finden Sie unter [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Vermeiden Sie nach Möglichkeit das Starten von Prozessen auf der Grundlage von Benutzereingaben.
- Überprüfen Sie die Eingabe anhand eines bekannten sicheren Satzes von Zeichen und Länge.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Wenn Sie wissen, dass die Eingabe als sicher überprüft wurde, können Sie diese Warnung sicher unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
