---
title: EditorConfig im Vergleich zu Analysetools
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408825"
---
# <a name="code-analysis-faq"></a>Häufig gestellte Fragen zur Codeanalyse

Diese Seite enthält Antworten auf einige häufig gestellte Fragen zur .NET Compiler Platform-basierten Codeanalyse in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Codeanalyse im Vergleich zu EditorConfig

**F:** Sollte ich die Codeanalyse oder EditorConfig zum Überprüfen des Codeformats verwenden?

**A**: Die Codeanalyse- und EditorConfig-Dateien arbeiten Hand in Hand. Wenn Sie Codeformate [in einer EditorConfig-Datei](../ide/editorconfig-code-style-settings-reference.md) oder auf der Seite für [Text-Editor-Optionen](../ide/code-styles-and-code-cleanup.md) definieren, konfigurieren Sie tatsächlich die in Visual Studio integrierten Codeanalysetools. EditorConfig-Dateien können verwendet werden, um Analysetoolregeln zu aktivieren oder zu deaktivieren und um einige NuGet-Analysetoolpakete wie [FxCop-Analysetools](configure-fxcop-analyzers.md) zu konfigurieren.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig im Vergleich zu Regelsätzen

**F:** Sollten meine Analysetools mithilfe eines Regelsatzes oder einer EditorConfig-Datei konfiguriert werden?

**A**: Regelsätze und EditorConfig-Dateien können gleichzeitig vorhanden sein und zum Konfigurieren von Analysetools verwendet werden. Sowohl EditorConfig-Dateien als auch Regelsätze ermöglichen das Aktivieren und Deaktivieren von Regeln und das Festlegen deren Schweregrads.

EditorConfig-Dateien bieten jedoch weitere Möglichkeiten zum Konfigurieren von Regeln:

- Für FxCop-Analysetools können Sie mit EditorConfig-Dateien [definieren, welche Arten von Code analysiert werden](fxcop-analyzer-options.md).
- In den in Visual Studio integrierten Analysetools für Codeformate können Sie mit EditorConfig-Dateien [die bevorzugten Codeformate für eine Codebasis definieren](../ide/editorconfig-code-style-settings-reference.md).

Zusätzlich zu Regelsätzen und EditorConfig-Dateien werden einige Analysetools durch die Verwendung von Textdateien konfiguriert, die als [zusätzliche Dateien](../ide/build-actions.md#build-action-values) für die C#- und VB-Compiler gekennzeichnet sind.

> [!NOTE]
> - EditorConfig-Dateien können nur zum Aktivieren von Regeln und Festlegen deren Schweregrads in Visual Studio 2019, Version 16.3 und höher verwendet werden.
> - EditorConfig-Dateien können nicht zum Konfigurieren der Legacyanalyse verwendet werden, wohingegen dies mit Regelsätzen möglich ist.

## <a name="code-analysis-in-ci-builds"></a>Codeanalyse in CI-Builds

**F:** Funktioniert die .NET Compiler Platform-basierte Codeanalyse in CI-Builds (Continuous Integration)?

**A**: Ja. Bei Analysetools, die von einem NuGet-Paket installiert werden, werden diese Regeln [zur Erstellungszeit (und während eines CI-Builds) erzwungen](roslyn-analyzers-overview.md#build-errors). Die in CI-Builds verwendeten Analysetools berücksichtigen die Regelkonfiguration für Regelsätze und EditorConfig-Dateien. Derzeit sind die in Visual Studio integrierten Codeanalysetools nicht als NuGet-Paket verfügbar, sodass diese Regeln in einem CI-Build nicht durchsetzbar sind.

## <a name="ide-analyzers-versus-stylecop"></a>IDE-Analysetools im Vergleich zu StyleCop

**F:** Worin besteht der Unterschied zwischen den IDE-Codeanalysetools in Visual Studio und StyleCop-Analysetools?

**A**: Die Visual Studio-IDE enthält integrierte Analysetools, die sowohl das Codeformat überprüfen als auch Qualitätsprobleme suchen. Diese Regeln helfen Ihnen, neue Sprachfeatures nach deren Einführung zu verwenden und die Verwaltbarkeit Ihres Codes zu verbessern. IDE-Analysetools werden ständig mit jeder Visual Studio-Version aktualisiert.

[StyleCop-Analysetools](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sind Analysetools von Drittanbietern, die als NuGet-Paket installiert werden und die Formatkonsistenz in Ihrem Code überprüfen. Im Allgemeinen können Sie mit StyleCop-Regeln persönliche Einstellungen für eine Codebasis festlegen, ohne ein bestimmtes Format zu empfehlen.

## <a name="code-analyzers-versus-legacy-analysis"></a>Codeanalysetools im Vergleich zur Legacyanalyse

**F:** Worin besteht der Unterschied zwischen der Legacyanalyse und der .NET Compiler Platform-basierten Codeanalyse?

**A**: Die .NET Compiler Platform-basierte Codeanalyse analysiert den Quellcode in Echtzeit und während der Kompilierung, wohingegen die Legacyanalyse Binärdateien analysiert, nachdem der Build abgeschlossen wurde. Weitere Informationen finden Sie unter [Quellcodeanalyse im Vergleich zur Legacyanalyse](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) und den [häufig gestellten Fragen zu FxCop-Analysetools](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Behandeln von Warnungen als Fehler

**F:** Mein Projekt verwendet die Buildoption, um Warnungen als Fehler zu behandeln. Nach der Migration von der Legacyanalyse zur Quellcodeanalyse werden alle Codeanalysewarnungen nun als Fehler angezeigt. Wie kann ich dies verhindern?

**A**: Führen Sie die folgenden Schritte aus, um zu verhindern, dass Codeanalysewarnungen als Fehler behandelt werden:

  1. Erstellen Sie eine PROPS-Datei mit dem folgenden Inhalt:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Fügen Sie der CSPROJ- oder VBPROJ-Projektdatei eine Zeile hinzu, um die im vorherigen Schritt erstellte PROPS-Datei zu importieren. Diese Zeile muss vor allen Zeilen platziert werden, in denen die PROPS-Dateien des FxCop-Analysetools importiert werden. Beispiel: Ihre PROPS-Datei wurde „codeanalysis.props“ genannt:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über Quellcode-Analysetools](roslyn-analyzers-overview.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
