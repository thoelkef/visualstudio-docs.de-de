---
title: FxCop-Codeanalyse und FxCop-Analysen
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136366"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Häufig gestellte Fragen zu FxCop und FxCop Analysen

Es kann etwas unübersichtlich werden, den Unterschieden zwischen legacy FxCop und FxCop Analysen. In diesem Artikel zielt darauf ab, um einige der Fragen, die Sie möglicherweise zu beheben.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Was ist der Unterschied zwischen legacy FxCop und FxCop Analyzer?

Ältere FxCop führt eine kompilierte Assembly nach dem Erstellen-Analysen. Es wird als eine separate ausführbare Datei ausgeführt **FxCopCmd.exe**. Lädt die kompilierte Assembly, Codeanalyse ausführt und dann die Analyseergebnisse FxCopCmd.exe (oder *Diagnose*).

FxCop-Analyzer basieren auf der .NET-compilerplattform ("Roslyn"). Sie [installieren Sie sie als NuGet-Paket](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) , auf das vom Projekt oder Projektmappe verwiesen wird. FxCop-Analysetools ausführen Quellcode basiert Analyse während der Ausführung der Compiler. FxCop-Analysen sind entweder innerhalb des Compilerprozesses gehostet **csc.exe** oder **vbc.exe**, und führen Sie Analysen ein, wenn das Projekt erstellt wird. Analyzer-Ergebnisse werden zusammen mit Compilerergebnisse gemeldet.

> [!NOTE]
> Sie können auch [FxCop-Analyzer als Visual Studio-Erweiterung installieren](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). In diesem Fall führen Sie die Analysetools, wie Sie im Code-Editor eingeben, aber sie nicht zum Zeitpunkt der Erstellung ausgeführt. Wenn Sie FxCop-Analysetools im Rahmen der continuous Integration (CI) ausführen möchten, installieren Sie diese stattdessen als NuGet-Paket.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Wird der Befehl für die Codeanalyse ausführen, die FxCop-Analysetools ausgeführt?

Nein. Bei der Auswahl **analysieren** > **Codeanalyse ausführen** in Visual Studio 2017 führt diese Analyse von statischem Code oder eine ältere FxCop. **Ausführen der Codeanalyse** hat keine Auswirkungen auf Roslyn basierenden Analysetools, einschließlich die FxCop auf Roslyn basierende Analysetools.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Wird die RunCodeAnalysis Msbuild-Projekt-Eigenschaft, die Analysen ausgeführt?

Nein. Die **RunCodeAnalysis** Eigenschaft in einer Projektdatei (z. B. *csproj*) wird nur verwendet, um ältere FxCop auszuführen. Es führt eine Post-Build-Msbuild-Aufgabe, die aufruft **FxCopCmd.exe**. Dies entspricht dem Auswählen von **analysieren** > **Codeanalyse ausführen** in Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Wie führe ich dann FxCop-Analysetools aus?

FxCop-Analysen, zuerst auszuführende [installieren Sie das NuGet-Paket](install-fxcop-analyzers.md) für sie. Anschließend erstellen Sie Ihr Projekt oder eine Projektmappe in Visual Studio oder mithilfe von Msbuild. Die Warnungen und Fehler, die die FxCop-Analysetools generieren werden angezeigt, der **Fehlerliste** oder im Befehlsfenster.

## <a name="see-also"></a>Siehe auch

- [Übersicht über die .NET Compiler Platform-Analysetools](roslyn-analyzers-overview.md)
- [Erste Schritte mit Analysen](fxcop-analyzers.yml)
- [Installieren von FxCop-Analysen](install-fxcop-analyzers.md)
