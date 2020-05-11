---
title: Deaktivieren der Codeanalyse
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431396"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Deaktivieren der Quellcodeanalyse für verwalteten Code

::: moniker range=">=vs-2019"

Auf dieser Seite können Sie die Codeanalyse in Visual Studio deaktivieren. Es gibt Einschränkungen für das, was Sie deaktivieren können, und das Verfahren zum Deaktivieren der Codeanalyse unterscheidet sich von einigen Faktoren:

- Projekttyp (.NET Core/Standard versus .NET Framework)

  .NET Core- und .NET Standard-Projekte verfügen über Optionen auf der Seite Codeanalyseeigenschaften, mit denen Sie die Codeanalyse von Analyzern deaktivieren können, die als NuGet-Paket installiert sind. Weitere Informationen finden Sie unter [.NET Core- und .NET Standard-Projekte](#net-core-and-net-standard-projects). Informationen zum Deaktivieren der Quellcodeanalyse für .NET Framework-Projekte finden Sie unter [.NET Framework-Projekte](#net-framework-projects).

- Quellanalyse im Vergleich zur Legacy-Analyse

  Dieses Thema gilt für die Quellcodeanalyse und nicht für die Legacyanalyse (binär). Informationen zum Deaktivieren der Legacyanalyse finden Sie unter [Gewusst wie: Aktivieren und Deaktivieren der Legacycodeanalyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.NET Core- und .NET Standard-Projekte

Ab Visual Studio 2019 Version 16.3 stehen auf der Seite Codeanalyseeigenschaften zwei Kontrollkästchen zur Verfügung, mit denen Sie steuern können, ob Analysatoren zur Buildzeit und Entwurfszeit ausgeführt werden. Diese Optionen sind projektspezifisch.

![Aktivieren oder Deaktivieren der Livecodeanalyse oder beim Erstellen in Visual Studio](media/run-on-build-run-live-analysis.png)

Um diese Seite zu öffnen, klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer,** und wählen Sie **Eigenschaften**aus. Wählen Sie die Registerkarte **Codeanalyse** aus.

- Um die Quellanalyse zur Buildzeit zu deaktivieren, deaktivieren Sie die Option **Beim Build ausführen.**
- Um die Live-Quellanalyse zu deaktivieren, deaktivieren Sie die Option **"Auf Live-Analyse ausführen".**

> [!NOTE]
> Ab Visual Studio 2019 Version 16.5 können Sie, wenn Sie den Bedarfscodeanalyseausführungsworkflow bevorzugen, die Ausführung von Analyzer während der Liveanalyse deaktivieren und/oder die Codeanalyse einmal in einem Projekt oder einer Projektmappe bei Bedarf manuell auslösen. Informationen zum manuellen Ausführen der Codeanalyse finden Sie unter [Gewusst wie: Ausführen der Codeanalyse manuell für verwalteten Code](how-to-run-code-analysis-manually-for-managed-code.md).  

## <a name="net-framework-projects"></a>.NET Framework-Projekte

Um die Quellcodeanalyse für Analysatoren zu deaktivieren, fügen Sie der [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file)eine oder mehrere der folgenden MSBuild-Eigenschaften hinzu.

| MSBuild-Eigenschaft | Beschreibung | Standard |
| - | - | - |
| `RunAnalyzersDuringBuild` | Steuert, ob Analysatoren zur Buildzeit ausgeführt werden. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Steuert, ob Analysatoren Code live zur Entwurfszeit analysieren. | `true` |
| `RunAnalyzers` | Deaktiviert Analysatoren sowohl zur Build- als auch zur Entwurfszeit. Diese Eigenschaft hat `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`Vorrang vor und . | `true` |

Beispiele:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Quellanalyse

Sie können die [Quellanalyse](roslyn-analyzers-overview.md) in Visual Studio 2017 nicht deaktivieren. Wenn Sie Analysefehler aus der Fehlerliste löschen möchten, können Sie alle aktuellen Verstöße unterdrücken, indem Sie in der Menüleiste die Option**Ausführen von Codeanalysen** **analysieren** > und aktive Probleme unterdrücken auswählen. Weitere Informationen finden Sie unter Unterdrücken von [Verstößen](use-roslyn-analyzers.md#suppress-violations).

Ab Visual Studio 2019 Version 16.3 können Sie die Quellcodeanalyse deaktivieren oder bei Bedarf ausführen. Erwägen Sie ein Upgrade auf Visual Studio 2019.

## <a name="legacy-analysis"></a>Legacyanalyse

Sie können die Legacy-Buildzeitanalyse auf der Eigenschaftenseite **Codeanalyse** deaktivieren. Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren und Deaktivieren der Legacycodeanalyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Unterdrücken von Verstößen](use-roslyn-analyzers.md#suppress-violations)
- [Gewusst wie: Aktivieren und Deaktivieren der Legacycodeanalyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
