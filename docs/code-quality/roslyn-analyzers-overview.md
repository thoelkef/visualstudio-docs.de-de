---
title: Roslyn-Analysetools in Visual Studio
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
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511421"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Übersicht über die .NET Compiler Platform-Analysetools

Visual Studio 2017 enthält einen integrierten Satz von .NET Compiler Platform-Analysetools, die von C#- oder Visual Basic-Code zu analysieren, während der Eingabe. Sie können zusätzliche Analysen als Visual Studio-Erweiterung, oder klicken Sie auf der Basis eines pro-Projekt als NuGet-Paket installieren. Analysetools Betrachten von Codeformat, Qualität des Codes und verwaltbarkeit, Codeentwurf und andere Probleme.

Wenn durch eine Analyse Regelverstöße gefunden werden, werden sie gemeldet sowohl im Code-Editor als eine *Wellenlinien* unter den fehlerhaften Code und in der **Fehlerliste**.

Viele Analyzer-Regeln oder *Diagnose*, haben Sie einen oder mehrere zugeordnete *Codekorrekturen* , die Sie anwenden können, um das Problem zu beheben. Der Analyzer-Diagnose, die in Visual Studio integriert sind haben eine zugehörige Code beheben. Mit dem Code werden angezeigt, klicken Sie im Menü Symbol Glühbirne sowie andere Arten von *Schnellaktionen*. Weitere Informationen zu diesen Codekorrekturen, finden Sie unter [häufig vorkommende Schnellaktionen](../ide/common-quick-actions.md).

![Verletzung der Analyzer und Codefehlerbehebung für die schnelle Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn-Analysetools und Analyse von statischem code

.NET Compiler Platform ("Roslyn") Analyzer ersetzt schließlich [Analyse von statischem Code](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele der Regeln für die statische Codeanalyse wurden bereits als Roslyn-Analyzer-Diagnose umgeschrieben.

Wie statische Analyse Verletzungen, Verletzungen der Roslyn-Analyzer angezeigt werden, der **Fehlerliste**. Darüber hinaus Verletzungen der Roslyn-Analyzer auch angezeigt im Code-Editor als *Unterstreichung* unter den fehlerhaften Code. Die Farbe von der Wellenlinie hängt die [schweregradeinstellung](../code-quality/use-roslyn-analyzers.md#rule-severity) der Regel. Der folgende Screenshot zeigt drei Verstöße&mdash;eine rote, eine Grün und einem grau dargestellt:

![Die Unterstreichung im Code-editor](media/diagnostics-severity-colors.png)

Roslyn-Analyzer analysieren von Code zur Buildzeit, z. B. die Analyse von statischem Code aktiviert ist, jedoch auch live während der Eingabe. Roslyn-Analysetools bieten auch während der Entwurfszeit-Analyse von Codedateien, die nicht im Editor geöffnet sind, wenn Sie aktivieren [vollständige projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Buildfehler und Warnungen von Roslyn-Analysetools werden nur angezeigt, wenn die Analyzer als NuGet-Paket installiert sind.

Roslyn-Analysetools melden dieselben Arten von Problemen, die Analyse von statischem Code ist jedoch, nicht nur, sondern sie erleichtern es Ihnen, eine oder alle Vorkommen des Verstoßes in der Datei oder das Projekt zu beheben. Diese Aktionen heißen *Codekorrekturen*. Mit dem Code werden die IDE-spezifische; in Visual Studio werden sie als implementiert [Schnellaktionen](../ide/quick-actions.md). Nicht alle Analyzer Diagnose haben eine Fehlerbehebung für die zugehörige Code.

> [!NOTE]
> Die Menüoption **analysieren** > **Codeanalyse ausführen** gilt nur statische Codeanalyse. Darüber hinaus auf des Projekts **Codeanalyse** auf der Seite die **Codeanalyse für Build aktivieren** und **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen gelten nur für Analyse von statischem Code. Sie haben keine Auswirkungen auf die Roslyn-Analysetools.

Zur Unterscheidung zwischen Verletzungen von Roslyn-Analysetools und Analyse von statischem Code in die **Fehlerliste**, sehen Sie sich die **Tool** Spalte. Wenn eine der Assemblys im Analyzer mit dem Tool-Wert übereinstimmt **Projektmappen-Explorer**, z. B. **Microsoft.CodeQuality.Analyzers**, die Verletzung von eines Roslyn-Analyzers stammt. Die Verletzung stammt, andernfalls Analyse von statischem Code.

![Tool-Spalte in der Fehlerliste](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>NuGet-Paket im Vergleich zu VSIX-Erweiterung

.NET Compiler Platform Analysen werden werden pro Projekt über ein NuGet-Paket oder Visual Studio gültigen als Visual Studio-Erweiterung installiert. Es gibt einige Verhaltensunterschiede zwischen diesen beiden Methoden der [Analyzer installieren](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Wenn Sie Analysetools wie Visual Studio-Erweiterung installieren, gelten sie für alle Instanzen von Visual Studio auf Projektmappenebene. Bei der Installation von die Analyzer als NuGet-Paket, die die bevorzugte Methode ist, gelten nur für das Projekt, in dem das NuGet-Paket installiert wurde. In teamumgebungen, Analysen, die als NuGet-Pakete installiert sind, im Bereich für *alle Entwickler* , die an diesem Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Installieren Sie Regeln erzwungen, die zur Buildzeit, z. B. über die Befehlszeile oder als Teil einer continuous Integration (CI) erstellen, dass die Analyzer als NuGet-Paket. Analyzer Warnungen und Fehler nicht im Buildbericht angezeigt, wenn Sie die Analyzer als eine Erweiterung installieren.

Der folgende Screenshot zeigt die Ausgabe erstellen über die Befehlszeile beim Erstellen eines Projekts, das einen Regelverstoß Analyzer enthält:

![MSBuild-Ausgabe Regelverstoß zugeordnet](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Regelschweregrad

Sie können nicht den Schweregrad der Regeln von Analysen festlegen, die als Visual Studio-Erweiterung installiert wurden. So konfigurieren Sie [Regel Schweregrad](../code-quality/use-roslyn-analyzers.md#rule-severity), die Analysen als NuGet-Paket zu installieren.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Installieren von Roslyn-Analysetools in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Verwenden von Roslyn-Analysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen in Visual Studio](../ide/quick-actions.md)
- [Schreiben Sie Ihren eigenen Roslyn-analyzer](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform-SDK](/dotnet/csharp/roslyn-sdk/)