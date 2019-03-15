---
title: "\"Editorconfig\" im Vergleich zu Analysen"
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874667"
---
# <a name="analyzers-faq"></a>FAQ zu Analysetools

Diese Seite enthält Antworten auf einige häufig gestellten Fragen zu Roslyn-Analysetools in Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Roslyn-Analysetools im Vergleich zu editorconfig

**Q**: Roslyn-Analysetools oder editorconfig für das Codeformat soll ich verwenden?

**A**: Roslyn-Analysetools und editorconfig-Dateien arbeiten Hand in Hand. Beim Definieren von Codeformate [in einer editorconfig-Datei](../ide/editorconfig-code-style-settings-reference.md) oder auf die [Text-Editor-Optionen](../ide/code-styles-and-quick-actions.md) Seite konfigurieren Sie tatsächlich die Roslyn-Analysetools, die in Visual Studio integriert sind. EditorConfig-Dateien können auch verwendet werden, um einige Pakete von Drittanbietern Analyzer zu konfigurieren, z. B. [FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>"Editorconfig" im Vergleich zu Regelsätzen

**Q**: Sollte ich meine Analysen mit einem Regelsatz oder eine editorconfig-Datei konfigurieren?

**A**: Regelsätze und editorconfig-Dateien sind sich gegenseitig ausschließende Möglichkeiten zum Konfigurieren von Analysen. Sie können gleichzeitig vorhanden sein. [-Regelsätze](analyzer-rule-sets.md) können Sie aktivieren oder Deaktivieren von Regeln aus, und legen Sie ihren Schweregrad. EditorConfig-Dateien bieten weitere Informationen zum Konfigurieren von Regeln. Editorconfig-Dateien für FxCop-Analyzer können Sie [definieren, welche Arten von Code zum Analysieren von](fxcop-analyzer-options.md). Editorconfig-Dateien für die Analyzer, die in Visual Studio integriert sind, können Sie [definieren Sie die bevorzugte Codeformate](../ide/editorconfig-code-style-settings-reference.md) für eine Codebasis.

Zusätzlich zu den Regelsätze und editorconfig-Dateien, manche Analysetools von Drittanbietern konfiguriert werden, durch die Verwendung von Textdateien als [zusätzliche Dateien](../ide/build-actions.md#build-action-values) für die C# - und VB-Compiler.

> [!NOTE]
> EditorConfig-Dateien können nicht verwendet werden, so konfigurieren Sie Regeln für die statische Codeanalyse, dagegen Regelsätze können.

## <a name="analyzers-in-ci-builds"></a>Analysetools in CI-builds

**Q**: Funktionieren die Analysetools in continuous Integration (CI)-Builds?

**A**: Ja. Für Analyzer, die aus einem NuGet-Paket installiert sind, werden diese Regeln [erzwungen, die zum Zeitpunkt der Erstellung](roslyn-analyzers-overview.md#build-errors), einschließlich während eines CI-Builds. Analysetools in CI-Builds Respekt-Regelkonfiguration aus beiden verwendet [-Regelsätze](analyzer-rule-sets.md) und [editorconfig-Dateien](configure-fxcop-analyzers.md). Derzeit werden die codeanalyzer, die in Visual Studio erstellt wurden, sind nicht verfügbar ist, als NuGet-Paket, und diese Regeln sind also nicht durchsetzbar, in einem CI-Build.

## <a name="ide-analyzers-versus-stylecop"></a>IDE-Analysetools im Vergleich zu StyleCop

**Q**: Was ist der Unterschied zwischen der IDE von Visual Studio Code-Analyzer und die StyleCop-Analyzer?

**A**: Visual Studio-IDE enthält integrierte Analysen, die für beide Stil und die Qualität von codeproblemen aussehen. Diese Regeln können Sie neue Sprachfeatures verwenden, wie sie eingeführt werden, und verbessern die Verwaltbarkeit des Codes. IDE-Analysetools werden fortlaufend aktualisiert, mit jeder Version von Visual Studio.

[StyleCop-Analysetools](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) Drittanbieter-Analyzer als NuGet-Paket installiert, die Konsistenz der Stil in Ihrem Code untersucht werden. Im Allgemeinen können mit StyleCop-Regeln Sie persönliche Einstellungen für einen Code Basis festlegen, ohne dabei einen Stil über ein anderes zu empfehlen.

## <a name="analyzers-versus-static-code-analysis"></a>Analysetools im Vergleich zur Analyse von statischem code

**Q**: Was ist der Unterschied zwischen Analyzer und Analyse von statischem Code?

**A**: Analysetools analysieren Quellcode in Echtzeit und während der Kompilierung, während der Analyse von statischem Code Binärdateien analysiert wird, nachdem der Build abgeschlossen wurde. Weitere Informationen finden Sie unter [Roslyn-Analysetools im Vergleich zu statischer Codeanalyse](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) und [FxCop-Analyzer – häufig gestellte Fragen](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Analysetools](roslyn-analyzers-overview.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)