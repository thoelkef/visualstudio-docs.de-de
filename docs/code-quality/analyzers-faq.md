---
title: EditorConfig versus Analysatoren
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300924"
---
# <a name="code-analysis-faq"></a>Häufig gestellte Fragen zur Codeanalyse

Diese Seite enthält Antworten auf einige häufig gestellte Fragen zur .NET Compiler Platform-basierten Codeanalyse in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Codeanalyse im Vergleich zu EditorConfig

**F**: Soll ich codeanalysis oder EditorConfig zum Überprüfen des Codestils verwenden?

**A**: Codeanalyse und EditorConfig-Dateien arbeiten Hand in Hand. Wenn Sie Codestile [in einer EditorConfig-Datei](../ide/editorconfig-code-style-settings-reference.md) oder auf der Seite [Texteditor-Optionen](../ide/code-styles-and-code-cleanup.md) definieren, konfigurieren Sie die Codeanalysatoren, die in Visual Studio integriert sind. EditorConfig-Dateien können verwendet werden, um Analyzer-Regeln zu aktivieren oder zu deaktivieren und auch einige NuGet-Analyzer-Pakete zu konfigurieren, z. B. [FxCop-Analysatoren](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus Regelsätze

**F**: Soll ich meine Analysatoren mit einem Regelsatz oder einer EditorConfig-Datei konfigurieren?

**A**: Regelsätze und EditorConfig-Dateien können nebeneinander bestehen und beide zum Konfigurieren von Analysatoren verwendet werden. Mit EditorConfig-Dateien und Regelsätzen können Sie Regeln aktivieren und deaktivieren und deren Schweregrad festlegen.

EditorConfig-Dateien bieten jedoch zusätzliche Möglichkeiten zum Konfigurieren von Regeln:

- Für FxCop-Analysatoren können Sie mit [EditorConfig-Dateien definieren, welche Codetypen analysiert werden sollen.](fxcop-analyzer-options.md)
- Für die Code-Style-Analyzer, die in Visual Studio integriert sind, können Sie mit [EditorConfig-Dateien die bevorzugten Codestile](../ide/editorconfig-code-style-settings-reference.md) für eine Codebasis definieren.

Zusätzlich zu Regelsätzen und EditorConfig-Dateien werden einige Analysatoren durch die Verwendung von Textdateien konfiguriert, die als [zusätzliche Dateien](../ide/build-actions.md#build-action-values) für die C- und VB-Compiler markiert sind.

> [!NOTE]
> - EditorConfig-Dateien können nur verwendet werden, um Regeln zu aktivieren und ihren Schweregrad in Visual Studio 2019 Version 16.3 und höher festzulegen.
> - EditorConfig-Dateien können nicht zum Konfigurieren von Legacyanalysen verwendet werden, während Regelsätze dies können.

## <a name="code-analysis-in-ci-builds"></a>Codeanalyse in CI-Builds

**F**: Funktioniert die auf der .NET Compiler Platform basierende Codeanalyse in Continuous Integration (CI)-Builds?

**A:** Ja. Für Analysatoren, die von einem NuGet-Paket installiert werden, werden diese Regeln [zur Buildzeit erzwungen,](roslyn-analyzers-overview.md#build-errors)auch während eines CI-Builds. Die in CI-Builds verwendeten Analyzer respektieren die Regelkonfiguration sowohl aus Regelsätzen als auch aus EditorConfig-Dateien. Derzeit sind die Codeanalysatoren, die in Visual Studio integriert sind, nicht als NuGet-Paket verfügbar, sodass diese Regeln in einem CI-Build nicht durchsetzbar sind.

## <a name="ide-analyzers-versus-stylecop"></a>IDE-Analysatoren im Vergleich zu StyleCop

**F**: Was ist der Unterschied zwischen den Visual Studio IDE-Codeanalysatoren und StyleCop-Analysatoren?

**A**: Die Visual Studio-IDE enthält integrierte Analysatoren, die sowohl nach Codestil- als auch nach Qualitätsproblemen suchen. Diese Regeln helfen Ihnen, neue Sprachfeatures bei der Einführung zu verwenden und die Wartbarkeit Ihres Codes zu verbessern. IDE-Analysatoren werden mit jeder Visual Studio-Version ständig aktualisiert.

[StyleCop-Analysatoren](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sind Drittanbieter-Analysatoren, die als NuGet-Paket installiert sind und die auf Stilkonsistenz in Ihrem Code überprüfen. Im Allgemeinen können Sie mit StyleCop-Regeln persönliche Einstellungen für eine Codebasis festlegen, ohne einen Stil gegenüber einem anderen zu empfehlen.

## <a name="code-analyzers-versus-legacy-analysis"></a>Codeanalysatoren im Vergleich zur Legacyanalyse

**F**: Was ist der Unterschied zwischen Legacyanalyse und .NET Compiler Platform-basierter Codeanalyse?

**A**: .NET Compiler Platform-based code analysis sanalysiert Quellcode in Echtzeit und während der Kompilierung, während die Legacyanalyse Binärdateien analysiert, nachdem der Build abgeschlossen wurde. Weitere Informationen finden Sie unter [.NET Compiler Platform-based analysis versus legacy analysis](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) and [FxCop analyzers FAQ](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

**F**: Mein Projekt verwendet die Buildoption, um Warnungen als Fehler zu behandeln. Nach der Migration von der Legacyanalyse zur Quellcodeanalyse werden nun alle Codeanalysewarnungen als Fehler angezeigt. Wie kann ich das verhindern?

**A**: Um zu verhindern, dass Codeanalysewarnungen als Fehler behandelt werden, führen Sie die folgenden Schritte aus:

  1. Erstellen Sie eine .props-Datei mit dem folgenden Inhalt:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Fügen Sie Ihrer .csproj- oder VBproj-Projektdatei eine Zeile hinzu, um die im vorherigen Schritt erstellte .props-Datei zu importieren. Diese Zeile muss vor allen Zeilen platziert werden, die die FxCop Analyzer .props Dateien importieren. Wenn Ihre .props-Datei beispielsweise codeanalysis.props heißt:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Weitere Informationen

- [Analyzer-Übersicht](roslyn-analyzers-overview.md)
- [.NET Codierungskonventionseinstellungen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
