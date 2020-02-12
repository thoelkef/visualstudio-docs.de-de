---
title: Codeanalyse mithilfe von Roslyn-Analysetools
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34225858e88f4ee969f0e51013bcdb04812d425f
ms.sourcegitcommit: a86ee68e3ec23869b6eaaf6c6b7946b1d9a88d01
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77144772"
---
# <a name="overview-of-source-code-analyzers"></a>Übersicht über Quellcode-Analysetools

Analysetools der .NET Compiler Platform („Roslyn“) analysieren Ihren C#- oder Visual Basic-Code auf Stil, Qualität und Verwaltbarkeit, Design und weitere Aspekte Ihres Codes.

- Einige Analysetools werden in Visual Studio integriert. Die Diagnose-ID oder der Code für diese Analysetools ist vom Format IDExxxx, z. B. IDE0067. Die meisten integrierten Analysetools überprüfen das [Codeformat](../ide/code-styles-and-code-cleanup.md), und Sie können auf der Seite mit den [Text-Editor-Optionen](../ide/code-styles-and-code-cleanup.md) oder in einer [EditorConfig-Datei](../ide/editorconfig-code-style-settings-reference.md) Einstellungen konfigurieren. Einige wenige integrierte Analysetools überprüfen die Qualität des Codes.

- Sie können aber auch zusätzliche Analysetools als Visual Studio-Erweiterung oder als NuGet-Paket installieren. Zum Beispiel:

  - [FxCop-Analysetools](../code-quality/install-fxcop-analyzers.md), die von Microsoft empfohlenen Analysetools für die Qualitätsanalyse des Codes
  - Analysetools von Drittanbietern wie [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/) und [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Wenn ein Analysetool Regelverstöße findet, werden sie im Code-Editor (als *Wellenlinie* unter dem fehlerhaften Code) und im Fenster „Fehlerliste“ angezeigt.

Viele Analysetoolregeln oder *Diagnosen* verfügen über mindestens ein *Codefix*, den Sie zur Problembehebung anwenden können. Den in Visual Studio integrierten Diagnoseanalysetools ist jeweils ein Codefix zugeordnet. Codekorrekturen werden zusammen mit anderen [schnellen Aktionen](../ide/quick-actions.md) im Fehlerbehebungsmenü (Glühbirnensymbol) angezeigt. Weitere Informationen zu diesen Codefixen finden Sie unter [Häufige schnelle Aktionen](../ide/common-quick-actions.md).

![Verstoß im Analysetool und Codefix mithilfe einer schnellen Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Quellcodeanalyse im Vergleich zur Legacyanalyse

Die Quellanalyse der Roslyn-Analysetools ersetzt die [Legacyanalyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele Regeln der Legacyanalyse wurden bereits als Roslyn-Codeanalysetools neu geschrieben. Die Legacyanalyse ist für neuere Projektvorlagen wie .NET Core- und .NET Standard-Projekte nicht verfügbar.

Wenn Verstöße bei der Quellcodeanalyse gefunden werden, werden diese ähnlich wie bei der Legacyanalyse im Fenster „Fehlerliste“ in Visual Studio angezeigt. Außerdem erscheinen Verstöße bei der Quellcodeanalyse auch im Code-Editor als *Wellenlinie* unter dem fehlerhaften Code. Die Farbe der Wellenlinie hängt von den [Schweregradeinstellungen](../code-quality/use-roslyn-analyzers.md#rule-severity) der Regel ab. Im folgenden Screenshot werden drei Verstöße angezeigt &mdash; einer rot, einer grün und einer grau:

![Wellenlinien im Code-Editor in Visual Studio](media/diagnostics-severity-colors.png)

Wie bei der Legacyanalyse (sofern aktiviert) wird Code von Codeanalysetools sowohl zur Buildzeit als auch live während der Eingabe analysiert. Wenn Sie die [vollständige Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis) aktivieren, stellen Codeanalysetools auch Entwurfszeitanalysen von Codedateien bereit, die nicht im Editor geöffnet sind.

> [!TIP]
> Buildfehler und Warnungen von Codeanalysetools werden nur angezeigt, wenn die Analysetools als NuGet-Paket installiert wurden. Die integrierten Analysetools wie IDE0067 und IDE0068 werden nie während des Buildvorgangs ausgeführt.

Roslyn-Codeanalysetools melden nicht nur die gleichen Problemtypen wie die Legacyanalyse, sie ermöglichen Ihnen auch die einfache Behebung eines oder aller Vorkommnisse von Verstößen in Ihrer Datei oder Ihrem Projekt. Diese Aktionen werden als *Codefixe* bezeichnet. Codekorrekturen sind IDE-spezifisch. In Visual Studio werden sie als [schnelle Aktionen](../ide/quick-actions.md) implementiert. Nicht allen Diagnoseanalysetools ist ein Codefix zugeordnet.

> [!NOTE]
> Die Menüoption **Analysieren** > **Codeanalyse ausführen** wird nur für die Legacyanalyse angewandt.

Sehen Sie sich die Spalte **Tool** an, um zwischen Verstößen durch Codeanalysetools und Verstößen durch Legacyanalyse in der Fehlerliste zu unterscheiden. Wenn der Tool-Wert mit einer der Assemblys des Analysetools im **Projektmappen-Explorer** übereinstimmt, z.B. **Microsoft.CodeQuality.Analyzers**, stammt der Verstoß von einem Codeanalysetool. Andernfalls stammt der Verstoß von einer Legacyanalyse.

![Tool-Spalte in Fehlerliste](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Die MSBuild-Eigenschaft **RunCodeAnalysis** in einer Projektdatei gilt nur für die Legacyanalyse. Legen Sie bei der Installation von Analysetools für **RunCodeAnalysis** in Ihrer Projektdatei **false** fest, um zu verhindern, dass die Legacyanalyse nach dem Buildvorgang ausgeführt wird.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet-Paket im Vergleich zur VSIX-Erweiterung

Roslyn-Codeanalysetools können mithilfe eines NuGet-Pakets pro Projekt installiert werden. Einige sind auch als Visual Studio-Erweiterung verfügbar. Dann können Sie sie in jeder Projektmappe anwenden, die Sie in Visual Studio öffnen. Es gibt einige grundsätzliche Verhaltensunterschiede zwischen diesen beiden Methoden zum [Installieren von Analysetools](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Wenn Sie Analysetools als Visual Studio-Erweiterung installieren, werden diese auf Projektmappenebene und für alle Instanzen von Visual Studio angewandt. Wenn Sie die Analysetools als NuGet-Paket installieren, was wir Ihnen empfehlen, werden die Tools nur für das Projekt angewandt, in dem das NuGet-Paket installiert wurde. Analysetools, die als NuGet-Pakete in Teamumgebungen installiert wurden, sind relevant für *alle Entwickler*, die an diesem Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Damit bei Buildzeit Regeln erzwungen werden, auch über die Befehlszeile oder als Teil eines Continuous Integration-Builds, installieren Sie die Analysetools als NuGet-Paket. Warnungen und Fehler der Analysetools erscheinen nicht im Buildbericht, wenn Sie die Analysetools als Erweiterung installieren.

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Regelverstoß des Analysetools enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Regelschweregrad

Den Regelschweregrad von Analysetools, die als Visual Studio-Erweiterung installiert wurden, können Sie nicht konfigurieren. Um den [Regelschweregrad](../code-quality/use-roslyn-analyzers.md#rule-severity) zu konfigurieren, installieren Sie die Analysetools als NuGet-Paket.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Installieren von Codeanalysetools in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [FAQ zu Analysetools](analyzers-faq.md)
- [Schreiben Ihres eigenen Codeanalysetools](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform-SDK](/dotnet/csharp/roslyn-sdk/)
