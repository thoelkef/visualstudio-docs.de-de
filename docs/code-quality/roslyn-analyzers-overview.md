---
title: Codeanalyse mithilfe von Roslyn-Analysetools
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 620f2905e2511ed403f0d25f32fa1bfc9b1eca68
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948841"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Übersicht über .NET Compiler Platform-Analysetools

Visual Studio 2017 enthält integrierte .NET Compiler Platform-Analysetools, die Ihren C#- und Visual Basic-Code während der Eingabe untersuchen. Analysetools untersuchen das Codeformat, die Qualität und Wartbarkeit des Codes, den Codeentwurf und andere Probleme. Sie können aber auch zusätzliche Analysetools als Visual Studio-Erweiterung oder projektbezogen als NuGet-Paket installieren.

Wenn von einem Analysetool Verstöße gegen Schwellenwertregeln gefunden werden, wird der fehlerhafte Code im Code-Editor mit einer *Wellenlinie* unterstrichen. Außerdem wird er in der **Fehlerliste** gemeldet.

Viele Analysetoolregeln oder *Diagnosen* verfügen über mindestens ein *Codefix*, den Sie zur Problembehebung anwenden können. Den in Visual Studio integrierten Diagnoseanalysetools ist jeweils ein Codefix zugeordnet. Codefixe werden zusammen mit anderen *schnellen Aktionen* im Fehlerbehebungsmenü (Glühbirnensymbol) angezeigt. Weitere Informationen zu diesen Codefixen finden Sie unter [Häufige schnelle Aktionen](../ide/common-quick-actions.md).

![Verstoß im Analysetool und Codefix mithilfe einer schnellen Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn-Analysetools im Vergleich zur statischen Codeanalyse

.NET Compiler Platform-Analysetools („Roslyn“) ersetzen letztendlich die [statische Codeanalyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele Regeln der statischen Codeanalyse wurden bereits als Roslyn-Diagnoseanalysetools neu geschrieben.

Wie auch Regelverstöße der statischen Codeanalyse werden Verstöße der Roslyn-Analysetools in der **Fehlerliste** angezeigt. Außerdem erscheinen Verstöße der Roslyn-Analysetools auch im Code-Editor als *Wellenlinie* unter dem fehlerhaften Code. Die Farbe der Wellenlinie hängt ab von den [Schweregradeinstellungen](../code-quality/use-roslyn-analyzers.md#rule-severity) der Regel. In dem folgenden Screenshot werden drei Verstöße&mdash; angezeigt (einer rot, einer grün und einer grau):

![Wellenlinien im Code-Editor](media/diagnostics-severity-colors.png)

Wie bei der statischen Codeanalyse auch, wenn diese aktiviert ist, wird Code von Roslyn-Analysetools zur Buildzeit untersucht. Dies jedoch auch live, während Sie tippen. Wenn Sie die [vollständige Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis) aktivieren, können Roslyn-Analysetools auch Entwurfszeitanalysen von Codedateien bereitstellen, die nicht im Editor geöffnet sind.

> [!NOTE]
> Buildfehler und Warnungen von Roslyn-Analysetools werden nur angezeigt, wenn die Analysetools als NuGet-Paket installiert wurden.

Roslyn-Analysetools melden nicht nur die gleichen Problemtypen wie die statische Codeanalyse, sie ermöglichen Ihnen auch die einfache Behebung eines oder aller Vorkommnisse von Verstößen in Ihrer Datei oder Ihrem Projekt. Diese Aktionen werden als *Codefixe* bezeichnet. Codefixe sind IDE-spezifisch; In Visual Studio werden sie als [schnelle Aktionen](../ide/quick-actions.md) implementiert. Nicht allen Diagnoseanalysetools ist ein Codefix zugeordnet.

> [!NOTE]
> Die Menüoption **Analysieren** > **Codeanalyse ausführen** wird nur für die statische Codeanalyse angewandt. Außerdem sind auf der **Codeanalyse**-Eigenschaftenseite eines Projekts die Kontrollkästchen **Codeanalyse für Build aktivieren** und **Ergebnisse aus generiertem Code unterdrücken** nur für die statische Codeanalyse relevant. Sie haben keine Auswirkungen auf Roslyn-Analysetools.

Um zwischen Verstößen durch Roslyn-Analysetools und Verstößen durch statische Codeanalyse in der **Fehlerliste** zu unterscheiden, sehen Sie sich die Spalte **Tool** an. Wenn der Tool-Wert mit einer der Assemblys des Analysetools im **Projektmappen-Explorer** übereinstimmt, z.B. **Microsoft.CodeQuality.Analyzers**, stammt der Verstoß von einem Roslyn-Analysetool. Andernfalls stammt der Verstoß von einer statischen Codeanalyse.

![Tool-Spalte in Fehlerliste](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>NuGet-Paket im Vergleich zur VSIX-Erweiterung

.NET Compiler Platform-Analysetools können projektbezogen über ein NuGet-Paket installiert werden oder produktübergreifend als Visual Studio-Erweiterung. Es gibt einige grundsätzliche Verhaltensunterschiede zwischen diesen beiden Methoden zum [Installieren von Analysetools](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Wenn Sie Analysetools als Visual Studio-Erweiterung installieren, werden diese auf Projektmappenebene für alle Instanzen von Visual Studio angewandt. Wenn Sie die Analysetools als NuGet-Paket installieren, was wir Ihnen empfehlen, werden die Tools nur für das Projekt angewandt, in dem das NuGet-Paket installiert wurde. Analysetools, die als NuGet-Pakete in Teamumgebungen installiert wurden, sind relevant für *alle Entwickler*, die an diesem Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Damit bei Buildzeit Regeln erzwungen werden, auch über die Befehlszeile oder als Teil eines Continuous Integration-Builds, installieren Sie die Analysetools als NuGet-Paket. Warnungen und Fehler der Analysetools erscheinen nicht im Buildbericht, wenn Sie die Analysetools als Erweiterung installieren.

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Analysetool-Regelverstoß enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Regelschweregrad

Den Regelschweregrad von Analysetools, die als Visual Studio-Erweiterung installiert wurden, können Sie nicht festlegen. Um den [Regelschweregrad](../code-quality/use-roslyn-analyzers.md#rule-severity) zu konfigurieren, installieren Sie die Analysetools als NuGet-Paket.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Installieren von Roslyn-Analysetools in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Verwenden von Roslyn-Analysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen in Visual Studio](../ide/quick-actions.md)
- [Schreiben Sie Ihr eigenes Roslyn-Analysetool](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform-SDK](/dotnet/csharp/roslyn-sdk/)