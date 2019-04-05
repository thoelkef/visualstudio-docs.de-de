---
title: 'CA3006: Code nach Prozess-Befehl-Injection-Anfälligkeiten überprüfen'
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018530"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Code nach Prozess-Befehl-Injection-Anfälligkeiten überprüfen

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht einen Process-Befehl.

## <a name="rule-description"></a>Regelbeschreibung

Achten Sie darauf von Befehl Injection-Angriffen, bei der Arbeit mit nicht vertrauenswürdigen Eingaben. Ein Befehl-Injection-Angriff kann schädliche Befehle auf das zugrunde liegende Betriebssystem, gefährden die Sicherheit und Integrität Ihres Servers ausführen.

Mit dieser Regel versucht, Eingaben von HTTP-Anforderungen, die einen Verarbeitungsbefehl erreichen zu finden.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die einen Prozess startet, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Vermeiden Sie wenn möglich, Starten von Prozessen, die auf Grundlage der Benutzereingabe.
- Überprüfen Sie die Eingabe anhand von einer bekannten, sicheren Gruppe von Zeichen und Länge.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie wissen, wurde die Eingabe überprüft oder mit Escapezeichen versehen, um sicherzugehen, ist es sicher, diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

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
