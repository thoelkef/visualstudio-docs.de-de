---
title: Roslyn-Analyzer in Visual Studio
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
ms.openlocfilehash: aaa989347744e015b90cca186c6aa9756dfe90fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Übersicht über .NET Compiler Platform-Analyzern

Visual Studio-2017 enthält einen integrierten Satz von .NET Compiler Platform-Analysen, die den C#- oder Visual Basic-Code zu analysieren, während der Eingabe. Sie können zusätzliche Analysen als Visual Studio-Erweiterung, oder klicken Sie auf der Basis eines pro-Projekt als ein NuGet-Paket installieren. Betrachten Sie Code-Stil, Codequalität und verwaltbarkeit Codeentwurf und andere Probleme Analysen.

Wenn Verletzungen von Schwellenwertregeln durch einen Analyzer gefunden werden, werden sie gemeldet sowohl im Codeeditor als eine *Wellenlinie* unter den fehlerhaften Code und in der **Fehlerliste**.

Viele Analyzer-Regeln oder *Diagnose*, haben Sie ein oder mehrere zugeordnete *code Korrekturen* angewendet werden können, um das Problem zu beheben. Der Analyzer-Diagnose, die in Visual Studio integriert werden haben eine zugeordnete Codekorrektur. Codekorrekturen werden angezeigt, klicken Sie im Menü Symbol Glühbirne zusammen mit anderen Typen von *Schnellaktionen*. Informationen zu diesen Updates Code finden Sie unter [Schnellaktionen des allgemeinen](../ide/common-quick-actions.md).

![Analyzer Verstoßes und Schnellaktions Codekorrektur](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Im Vergleich zu statischer Codeanalyse Roslyn-Analyzern

Analysen für .NET Compiler Platform ("Roslyn") werden schließlich ersetzt [statische Codeanalyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele der Analyseregeln für statischen Code wurden bereits als Roslyn Analyzer Diagnose umgeschrieben.

Wie Verletzungen von Schwellenwertregeln von statischem Code Analysis, Verletzungen der Roslyn-Analyzer angezeigt werden, der **Fehlerliste**. Darüber hinaus Roslyn Analyzer Verstöße auch angezeigt im Codeeditor als *Unterstreichung* unter den fehlerhaften Code. Die Farbe von der Wellenlinie hängt die [schweregradeinstellung](../code-quality/use-roslyn-analyzers.md#rule-severity) der Regel. Der folgende Screenshot zeigt drei Verstöße&mdash;eine rote, eine Grün und einem grau dargestellt:

![Unterstreichung im Code-editor](media/diagnostics-severity-colors.png)

Roslyn-Analyzer analysieren von Code zur Buildzeit wie statische Codeanalyse aktiviert ist, jedoch auch live während der Eingabe! Roslyn-Analysen bietet auch zur Entwurfszeit Analyse von Codedateien an, die nicht im Editor geöffnet sind, wenn Sie aktivieren [vollständige projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Buildfehler und Warnungen aus Roslyn Analysen werden nur angezeigt, wenn Analysen als NuGet-Paket installiert sind.

Nicht nur melde Roslyn-Analyzern dieselbe Art von Problemen, die Analyse von statischem Code ausführt, sondern sie erleichtern es Ihnen, eine oder alle Vorkommen der Verstoß innerhalb einer Datei oder einem Projekt zu beheben. Diese Aktionen heißen *code Korrekturen*. Codekorrekturen sind IDE-spezifische; in Visual Studio implementiert als [Schnellaktionen](../ide/quick-actions.md). Nicht alle Analyzer Diagnosen haben eine zugeordnete Codekorrektur.

> [!NOTE]
> Die Menüoption **analysieren** > **Ausführen der Codeanalyse** gilt nur für statische Codeanalyse aus. Darüber hinaus an einem Projekt **Codeanalyse** auf der Seite der **Codeanalyse für Build aktivieren** und **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen gelten nur für statische Codeanalyse aus. Sie haben keine Auswirkung auf Roslyn-Analysen.

Unterscheidung zwischen Verletzungen von Roslyn-Analysen und statische Codeanalyse in die **Fehlerliste**, sehen Sie sich die **Tool** Spalte. Wenn eine der Assemblys im Analyzer mit dem Tool Wert übereinstimmt **Projektmappen-Explorer**, z. B. **Microsoft.CodeQuality.Analyzers**, einer Verletzung ergibt sich aus einem Roslyn-Analyseprogramm. Statische Codeanalyse hingegen stammt die Verletzung.

![Tool-Spalte in der Fehlerliste](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>NuGet-Paket im Vergleich mit der Erweiterung

.NET Compiler Platform Analysen werden installiert über ein NuGet-Paket oder eine Visual Studio-Wide pro Projekt als Visual Studio-Erweiterung. Es gibt einige wichtige Verhaltensunterschiede zwischen diesen beiden Methoden der [installieren Analyzer](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Gelten bei der Installation von Analysen als Visual Studio-Erweiterung für alle Instanzen von Visual Studio auf der Ebene Lösung. Bei der Installation von Analysen als NuGet-Paket, die die bevorzugte Methode ist, gelten nur für das Projekt, in dem das NuGet-Paket installiert wurde. Im Team-Umgebungen, Analysen, die als NuGet-Pakete installiert sind, im Bereich für *alle Entwickler* , die auf dieses Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Installieren Sie Analysen als NuGet-Paket, um Regeln zur Buildzeit, einschließlich der über die Befehlszeile oder als Teil einer continuous Integration (CI)-Build erzwungen haben. Analyzer Warnungen und Fehler nicht im Buildbericht angezeigt, wenn Analysen als Erweiterung zu installieren.

Der folgende Screenshot zeigt die Ausgabe erstellen über die Befehlszeile erstellen ein Projekt, ein Verstoß gegen eine Codeanalyseregel Analyzer enthält:

![MSBuild-Ausgabe mit Verstoß gegen eine Codeanalyseregel](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Schweregrad der Regel

Sie können nicht den Schweregrad der Regeln aus Analysen festlegen, die als Visual Studio-Erweiterung installiert wurden. So konfigurieren Sie [Regel "Schweregrad"](../code-quality/use-roslyn-analyzers.md#rule-severity), Analysen als ein NuGet-Paket installieren.

## <a name="next-steps"></a>Nächste Schritte

- [Roslyn-Analyzer in Visual Studio installieren](../code-quality/install-roslyn-analyzers.md)
- [Verwenden Sie Roslyn-Analyzer in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen in Visual Studio](../ide/quick-actions.md)
- [Schreiben Sie eigener Roslyn-analyzer](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)