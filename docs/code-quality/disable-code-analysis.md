---
title: Code Analyse deaktivieren
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d25254cabecd88c6e876646c3c276503aadf7eb7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587666"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Deaktivieren der Quell Code Analyse für verwalteten Code

::: moniker range=">=vs-2019"

Auf dieser Seite können Sie die Code Analyse in Visual Studio deaktivieren. Es gelten Einschränkungen für das, was Sie deaktivieren können, und die Vorgehensweise zum Ausschalten der Code Analyse variiert je nach den folgenden Faktoren:

- Projekttyp (.net Core/Standard im Vergleich zu .NET Framework)

  .Net Core-und .NET Standard-Projekte verfügen über Optionen auf der Seite mit den Code Analyse Eigenschaften, mit denen Sie die Code Analyse von Analyzern deaktivieren können, die als nuget-Paket installiert wurden. Weitere Informationen finden Sie unter [.net Core-und .NET Standard-Projekte](#net-core-and-net-standard-projects). Informationen zum Deaktivieren der Quell Code Analyse für .NET Framework Projekte finden Sie unter [.NET Framework Projekte](#net-framework-projects).

- Nuget Analyzer-Paket im Vergleich zu VSIX-oder integrierten Analyzern

  Derzeit ist es nicht möglich, die Live-Code Analyse für die integrierten Analyzers (z. b. Regel-ID IDE0067) zu deaktivieren. Ebenso ist es nicht möglich, die Live Code Analyse für Analysen zu deaktivieren, die als Teil einer Visual Studio-Erweiterung (VSIX) installiert wurden. Wenn Sie Fehler und Warnungen von integrierten und VSIX-basierten Analysemodulen unterdrücken möchten, wählen Sie in der Menüleiste die Option " **analysieren** > **Erstellen und unterdrücken von aktiven Problemen** " aus. Sie *können* die Live-und die integrierte Analyse für Analysen deaktivieren, die als Teil eines nuget-Pakets installiert sind.

- Quell Analyse und Legacy Analyse

  Dieses Thema bezieht sich auf die Quell Code Analyse und nicht auf die Legacy-(binäre) Analyse. Weitere Informationen zum Deaktivieren der Legacy Analyse finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.Net Core-und .NET Standard-Projekte

Ab Visual Studio 2019 Version 16,3 stehen auf der Seite mit den Code Analyse Eigenschaften zwei Kontrollkästchen zur Verfügung, mit denen Sie steuern können, ob nuget-basierte Analysen zum Zeitpunkt der Erstellung und zur Entwurfszeit ausgeführt werden. Diese Optionen sind projektspezifisch.

![Aktivieren oder Deaktivieren der Live Code Analyse oder bei der Erstellung in Visual Studio](media/run-on-build-run-live-analysis.png)

Um diese Seite zu öffnen, klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Wählen Sie die Registerkarte **Code Analyse** aus.

- Zum Deaktivieren der Quell Analyse während der Buildzeit deaktivieren Sie die Option **bei Build ausführen** .
- Um die Live Quell Analyse zu deaktivieren, deaktivieren Sie die Option **bei Live Analyse ausführen** .

> [!NOTE]
> Integrierte und auf VSIX basierende Analysen bieten weiterhin Live Analysen Ihres Codes, auch wenn die aktive **Analyse** nicht aktiviert ist. Wenn Sie Fehler und Warnungen von diesen Analysemodulen unterdrücken möchten, wählen Sie in der Menüleiste die Option zum **analysieren** > **Erstellen und unterdrücken aktiver Probleme** aus.

## <a name="net-framework-projects"></a>.NET Framework Projekte

Fügen Sie der [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file)mindestens eine der folgenden MSBuild-Eigenschaften hinzu, um die Quell Code Analyse für Analysen zu deaktivieren, die als Teil eines nuget-Pakets installiert sind.

| MSBuild-Eigenschaft | Beschreibung | Default |
| - | - | - |
| `RunAnalyzersDuringBuild` | Steuert, ob nuget-basierte Analysen zum Zeitpunkt der Erstellung ausgeführt werden. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Steuert, ob nuget-basierte Analysen Code zur Entwurfszeit Live analysieren. | `true` |
| `RunAnalyzers` | Deaktiviert nuget-basierte Analysen sowohl bei der Erstellung als auch bei der Entwurfszeit. Diese Eigenschaft hat Vorrang vor `RunAnalyzersDuringBuild` und `RunAnalyzersDuringLiveAnalysis`. | `true` |

Beispiele:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Quellanalyse

Sie können die [Quell Analyse](roslyn-analyzers-overview.md) in Visual Studio 2017 nicht deaktivieren. Wenn Sie Analysefehler aus dem Fehlerliste löschen möchten, können Sie alle aktuellen Verstöße unterdrücken, indem Sie in der Menüleiste **analysieren** > **Code Analyse ausführen und aktive Probleme unterdrücken** auswählen. Weitere Informationen finden Sie unter unter [drücken von Verletzungen](use-roslyn-analyzers.md#suppress-violations).

Ab Visual Studio 2019 Version 16,3 können Sie die nuget-basierte Quell Code Analyse deaktivieren. Sie sollten ein Upgrade auf Visual Studio 2019 durchführen.

## <a name="legacy-analysis"></a>Legacyanalyse

Sie können die Legacy-und buildzeitanalyse auf der Eigenschaften Seite für die **Code Analyse** deaktivieren. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Verstöße unterdrücken](use-roslyn-analyzers.md#suppress-violations)
- [Gewusst wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
