---
title: Codeanalyse mithilfe von Roslyn-Analysetools
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d4a9bfca972f9c57688b19bd872b31ee5997f76
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550765"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>Übersicht über .NET Compiler Platform-Codeanalysetools

Analysetools der .NET Compiler Platform („Roslyn“) analysieren Stil, Qualität und Verwaltbarkeit, Design und weitere Aspekte Ihres Codes. Visual Studio enthält integrierte Analysetools, die Ihren C#- und Visual Basic-Code während der Eingabe untersuchen. Die Einstellungen für diese integrierten Analysetools können Sie auf der Seite mit den [Text-Editor-Optionen](../ide/code-styles-and-code-cleanup.md) oder in einer Datei vom Typ [.editorconfig](../ide/editorconfig-code-style-settings-reference.md) konfigurieren. Sie können aber auch zusätzliche Analysetools als Visual Studio-Erweiterung oder als NuGet-Paket installieren.

Wenn von einem Analysetool Regelverstöße gefunden werden, wird der Code im Code-Editor mit einer *Wellenlinie* unterstrichen. Außerdem wird er im Fenster **Fehlerliste** gemeldet.

Viele Analysetoolregeln oder *Diagnosen* verfügen über mindestens ein *Codefix*, den Sie zur Problembehebung anwenden können. Den in Visual Studio integrierten Diagnoseanalysetools ist jeweils ein Codefix zugeordnet. Codekorrekturen werden zusammen mit anderen [schnellen Aktionen](../ide/quick-actions.md) im Fehlerbehebungsmenü (Glühbirnensymbol) angezeigt. Weitere Informationen zu diesen Codefixen finden Sie unter [Häufige schnelle Aktionen](../ide/common-quick-actions.md).

![Verstoß im Analysetool und Codefix mithilfe einer schnellen Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>.NET Compiler Platform-basierte Analyse im Vergleich zu Legacyanalyse

.NET Compiler Platform-Codeanalyse („Roslyn“) wird in Zukunft die [Legacyanalyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code ersetzen. Viele der Legacyanalyseregeln wurden bereits in .NET Compiler Platform-basierte Codeanalysen umgeschrieben.

Wie bei Verstößen von Legacyanalyseregeln werden auch bei der .NET Compiler Platform-basierten Codeanalyse Verstöße im Fenster „Fehlerliste“ in Visual Studio angezeigt. Außerdem werden Verstöße der .NET Compiler Platform-basierten Codeanalyse auch im Code-Editor als *Wellenlinien* unter dem fehlerhaften Code angezeigt. Die Farbe der Wellenlinie hängt von den [Schweregradeinstellungen](../code-quality/use-roslyn-analyzers.md#rule-severity) der Regel ab. In dem folgenden Screenshot werden drei Verstöße&mdash; angezeigt (einer rot, einer grün und einer grau):

![Wellenlinien im Code-Editor](media/diagnostics-severity-colors.png)

Wie bei der Legacyanalyse (sofern aktiviert) wird Code von .NET Compiler Platform-basierten Codeanalysetools sowohl zur Buildzeit als auch live während der Eingabe analysiert. Wenn Sie die [vollständige Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis) aktivieren, stellen Codeanalysetools auch Entwurfszeitanalysen von Codedateien bereit, die nicht im Editor geöffnet sind.

> [!TIP]
> Buildfehler und Warnungen von Codeanalysetools werden nur angezeigt, wenn die Analysetools als NuGet-Paket installiert wurden.

.NET Compiler Platform-basierte Codeanalysetools melden nicht nur die gleichen Problemtypen wie die Legacyanalyse, sie ermöglichen Ihnen auch die einfache Behebung eines oder aller Vorkommnisse von Verstößen in Ihrer Datei oder Ihrem Projekt. Diese Aktionen werden als *Codefixe* bezeichnet. Codefixe sind IDE-spezifisch; In Visual Studio werden sie als [schnelle Aktionen](../ide/quick-actions.md) implementiert. Nicht allen Diagnoseanalysetools ist ein Codefix zugeordnet.

> [!NOTE]
> Die folgenden UI-Optionen gelten nur für die Legacyanalyse:
>
> - Die Menüoption **Analysieren** > **Codeanalyse ausführen**.
> - Die Kontrollkästchen **Codeanalyse für Build aktivieren** und **Ergebnisse aus generiertem Code unterdrücken** auf der Registerkarte **Codeanalyse** der Eigenschaftenseiten eines Projekts.

Um zwischen Verstößen durch Codeanalysetools und Verstößen durch Legacyanalyse im Fenster „Fehlerliste“ zu unterscheiden, sehen Sie sich die Spalte **Tool** an. Wenn der Tool-Wert mit einer der Assemblys des Analysetools im **Projektmappen-Explorer** übereinstimmt, z.B. **Microsoft.CodeQuality.Analyzers**, stammt der Verstoß von einem Codeanalysetool. Andernfalls stammt der Verstoß von einer Legacyanalyse.

![Tool-Spalte in Fehlerliste](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Die MSBuild-Eigenschaft **RunCodeAnalysis** in einer Projektdatei gilt nur für die Legacyanalyse. Legen Sie bei der Installation von Analysetools für **RunCodeAnalysis** in Ihrer Projektdatei **false** fest, um zu verhindern, dass die Legacyanalyse nach dem Buildvorgang ausgeführt wird.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet-Paket im Vergleich zur VSIX-Erweiterung

.NET Compiler Platform-Analysetools können projektbezogen über ein NuGet-Paket installiert werden oder produktübergreifend als Visual Studio-Erweiterung. Es gibt einige grundsätzliche Verhaltensunterschiede zwischen diesen beiden Methoden zum [Installieren von Analysetools](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Wenn Sie Analysetools als Visual Studio-Erweiterung installieren, werden diese auf Projektmappenebene für alle Instanzen von Visual Studio angewandt. Wenn Sie die Analysetools als NuGet-Paket installieren, was wir Ihnen empfehlen, werden die Tools nur für das Projekt angewandt, in dem das NuGet-Paket installiert wurde. Analysetools, die als NuGet-Pakete in Teamumgebungen installiert wurden, sind relevant für *alle Entwickler*, die an diesem Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Damit bei Buildzeit Regeln erzwungen werden, auch über die Befehlszeile oder als Teil eines Continuous Integration-Builds, installieren Sie die Analysetools als NuGet-Paket. Warnungen und Fehler der Analysetools erscheinen nicht im Buildbericht, wenn Sie die Analysetools als Erweiterung installieren.

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Analysetool-Regelverstoß enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Regelschweregrad

Den Regelschweregrad von Analysetools, die als Visual Studio-Erweiterung installiert wurden, können Sie nicht festlegen. Um den [Regelschweregrad](../code-quality/use-roslyn-analyzers.md#rule-severity) zu konfigurieren, installieren Sie die Analysetools als NuGet-Paket.

## <a name="categories"></a>Kategorien

Nachstehend finden Sie die verschiedenen Arten von Analysetools, die Ihnen bei der Analyse Ihres Codes helfen:

- Von Microsoft empfohlene Analysetools: [FxCop-Analysetools](../code-quality/fxcop-analyzers.yml)
- Visual Studio IDE-Analysetools: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analysetools von Drittanbietern: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Installieren von Codeanalysetools in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [FAQ zu Analysetools](analyzers-faq.md)
- [Schreiben Ihres eigenen Codeanalysetools](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform-SDK](/dotnet/csharp/roslyn-sdk/)
