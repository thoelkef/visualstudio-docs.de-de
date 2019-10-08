---
title: Editor config und Analysen
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aec8c26a827a39abdfeacfc0e3d6dea4a62db43
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999977"
---
# <a name="code-analysis-faq"></a>FAQ zur Code Analyse

Diese Seite enthält Antworten auf einige häufig gestellte Fragen zur .NET Compiler Platform basierten Code Analyse in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Code Analyse im Vergleich zu Editor config

**F**: Sollte ich die Code Analyse oder editorconfig zum Überprüfen des Code Formats verwenden?

**A**: Code Analyse-und Editor config-Dateien arbeiten Hand in Hand. Wenn Sie Code Stile [in einer editorconfig-Datei](../ide/editorconfig-code-style-settings-reference.md) oder auf der [Options Seite Text-Editor](../ide/code-styles-and-code-cleanup.md) definieren, konfigurieren Sie tatsächlich die in Visual Studio integrierten Code-Analysen. Editor config-Dateien können auch verwendet werden, um einige nuget Analyzer-Pakete (z. b. [FxCop-Analysen](configure-fxcop-analyzers.md)) zu konfigurieren.

## <a name="editorconfig-versus-rule-sets"></a>Editor config im Vergleich zu Regelsätzen

**F**: Sollten meine Analysen mithilfe eines Regelsatzes oder einer Editor config-Datei konfiguriert werden?

**A**: Regelsätze und Editor config-Dateien können gleichzeitig vorhanden sein und können zum Konfigurieren von Analysemodulen verwendet werden. [Regelsätze](analyzer-rule-sets.md) ermöglichen das Aktivieren und Deaktivieren von Regeln und das Festlegen Ihres schwere Grads. Editor config-Dateien bieten andere Möglichkeiten zum Konfigurieren von Regeln. Für FxCop-Analyzers können Sie mit Editor config-Dateien [definieren, welche Arten von Code analysiert](fxcop-analyzer-options.md)werden. Bei den Code-Formatvorlagen, die in Visual Studio integriert sind, können Sie mit Editor config-Dateien [die bevorzugten Code Stile für eine Codebasis definieren](../ide/editorconfig-code-style-settings-reference.md) .

Zusätzlich zu den Regelsätzen und Editor config-Dateien werden einige Analysen durch die Verwendung von Textdateien konfiguriert, die als [zusätzliche Dateien](../ide/build-actions.md#build-action-values) für C# die Compiler-und VB-Compiler gekennzeichnet sind.

> [!NOTE]
> Editor config-Dateien können nicht zum Konfigurieren der Legacy Analyse verwendet werden, wohingegen Regelsätze dies möglich macht.

## <a name="code-analysis-in-ci-builds"></a>Code Analyse in CI-Builds

**F**: Funktioniert die .NET Compiler Platform basierte Code Analyse in Continuous Integration (CI)-Builds?

**A**: Ja. Bei Analysemodulen, die von einem nuget-Paket installiert werden, werden diese Regeln [zur Buildzeit erzwungen](roslyn-analyzers-overview.md#build-errors), einschließlich während eines CI-Builds. Die in CI verwendeten Analyzers erstellen die Regel Konfiguration sowohl aus [Regelsätzen](analyzer-rule-sets.md) als auch aus [Editor config-Dateien](configure-fxcop-analyzers.md). Derzeit sind die in Visual Studio integrierten Code Analysen nicht als nuget-Paket verfügbar, sodass diese Regeln in einem CI-Build nicht durchsetzbar sind.

## <a name="ide-analyzers-versus-stylecop"></a>IDE-Analysen im Vergleich zu StyleCop

**F**: Worin besteht der Unterschied zwischen den Visual Studio-IDE-Code-Analyzern und StyleCop-Analyzern?

**A**: Die Visual Studio-IDE enthält integrierte Analysen, die sowohl Code-als auch Qualitätsprobleme suchen. Diese Regeln helfen Ihnen, neue sprach Features zu verwenden, wenn Sie eingeführt werden, und die Wartbarkeit Ihres Codes zu verbessern. IDE-Analysen werden ständig mit jeder Visual Studio-Version aktualisiert.

[StyleCop-Analysen](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sind Analysen von Drittanbietern, die als nuget-Paket installiert werden und die Stilkonsistenz in Ihrem Code überprüfen. Im Allgemeinen können Sie mit StyleCop-Regeln persönliche Einstellungen für eine Codebasis festlegen, ohne einen Stil über einen anderen zu empfehlen.

## <a name="code-analyzers-versus-legacy-analysis"></a>Code Analysetools und Legacy Analyse

**F**: Worin besteht der Unterschied zwischen der Legacy Analyse und der .NET Compiler Platform basierten Code Analyse?

**A**: die .NET Compiler Platform basierte Code Analyse analysiert den Quellcode in Echtzeit und während der Kompilierung, während die Legacy Analyse Binärdateien analysiert, nachdem der Build abgeschlossen wurde. Weitere Informationen finden Sie unter [.NET Compiler Platform-basierte Analyse](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) und häufig gestellte Fragen zu den [FxCop-Analysen](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

**F**: Mein Projekt verwendet die Build-Option, um Warnungen als Fehler zu behandeln. Nach der Migration von der Legacy Analyse zur Quell Code Analyse werden alle Code Analyse Warnungen nun als Fehler angezeigt. Wie kann ich dies verhindern?

**A**: Führen Sie die folgenden Schritte aus, um zu verhindern, dass Code Analyse Warnungen als Fehler behandelt werden:

  1. Erstellen Sie eine.-Eigenschaften Datei mit folgendem Inhalt:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Fügen Sie der CSPROJ-oder VBPROJ-Projektdatei eine Zeile hinzu, um die im vorherigen Schritt erstellte Eigenschaften Datei zu importieren. Diese Zeile muss vor allen Zeilen platziert werden, in denen die FxCop Analyzer.-Eigenschaften Dateien importiert werden. Beispiel: Wenn die Datei ".-Eigenschaften" den Namen "CodeAnalysis.-Eigenschaften" hat:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über Analyzers](roslyn-analyzers-overview.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
