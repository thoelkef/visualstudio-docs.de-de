---
title: FxCop-Codeanalyse und FxCop-Analysetools
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431364"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Häufig gestellte Fragen zu FxCop und FxCop-Analysetools

Die Unterschiede zwischen Legacy-FxCop und FxCop-Analysetools können verwirrend sein. Deshalb werden in diesem Artikel einige Fragen behandelt, die Sie möglicherweise haben.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Was ist der Unterschied zwischen Legacy-FxCop und FxCop-Analysetools?

Legacy-FxCop führt die Analyse einer kompilierten Assembly nach dem Erstellen aus. Eine separate ausführbare Datei namens **FxCopCmd.exe** wird ausgeführt. Die Datei „FxCopCmd.exe“ lädt die kompilierte Assembly, führt die Codeanalyse aus und meldet dann die Ergebnisse (bzw. *Diagnose*).

FxCop-Analysetools basieren auf der .NET Compiler Platform („Roslyn“). Sie [installieren sie als NuGet-Pakete](install-fxcop-analyzers.md#nuget-package), auf die von dem Projekt oder der Projektmappe verwiesen wird. FxCop-Analysetools führen während der Ausführung des Compilers Analysen aus, die auf dem Quellcode basieren. FxCop-Analysetools werden im Compilerprozess gehostet, entweder **csc.exe** oder **vbc.exe**, und führen die Analyse bei der Erstellung des Projekts aus. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

> [!NOTE]
> Sie können [FxCop-Analysetools auch als Visual Studio-Erweiterung installieren](install-fxcop-analyzers.md#vsix). In diesem Fall werden die Analysetools ausgeführt, während Sie in den Code-Editor schreiben. Allerdings werden Sie nicht zum Zeitpunkt der Erstellung ausgeführt. Wenn Sie FxCop-Analysetools als Teil der CI (Continuous Integration) ausführen möchten, installieren Sie sie stattdessen als NuGet-Pakete.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Werden FxCop-Analysetools mit dem Befehl „Codeanalyse ausführen“ ausgeführt?

Vor der Veröffentlichung Visual Studio 2019 16.5 führt die Option **Ausführen** > **von Codeanalysen**analysieren eine Legacyanalyse aus. Wenn Sie Visual Studio 2019 16.5 starten, führt die Menüoption **Codeanalyse ausführen** Roslyn-basierte Analysatoren für das ausgewählte Projekt oder die ausgewählte Projektmappe aus. Wenn Sie Roslyn-basierte FxCop-Analysatoren installiert haben, würden sie auch ausgeführt. Weitere Informationen finden Sie unter [Gewusst wie: Ausführen der Codeanalyse manuell für verwalteten Code](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Werden Analysetools von der MSBuild-Projekteigenschaft „RunCodeAnalysis“ ausgeführt?

Nein. Die Eigenschaft **RunCodeAnalysis** in einer Projektdatei (z.B. *.csproj*) wird nur zum Ausführen von Legacy-FxCop verwendet. Sie führt eine MSBuild-Postbuildaufgabe aus, die **FxCopCmd.exe** aufruft.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Wie kann ich FxCop-Analysetools ausführen?

Zum Ausführen von FxCop-Analysetools müssen Sie zunächst die entsprechenden [NuGet-Pakete installieren](install-fxcop-analyzers.md). Dann erstellen Sie Ihr Projekt oder Ihre Projektmappe mit Visual Studio oder MSBuild. Die Warnungen und Fehlermeldungen von FxCop-Analysetools werden in der **Fehlerliste** oder im Befehlsfenster angezeigt.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Nach der Installation des NuGet-Pakets für das FxCop-Analysetool erhalte ich die Warnung „CA0507“.

Wenn Sie FxCop-Analysatoren installiert haben, aber weiterhin die Warnung **""Codeanalyse ausführen" erhalten, wurde zugunsten von FxCop-Analysatoren veraltet, die während des Builds ausgeführt werden",** müssen Sie möglicherweise die **RunCodeAnalysis** msbuild-Eigenschaft in Ihrer [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file) auf **false**festlegen. Andernfalls wird die Legacyanalyse nach jedem Build ausgeführt.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Welche Regeln wurden auf FxCop-Analysatoren portiert?

Informationen darüber, welche Legacyanalyseregeln auf [FxCop-Analysatoren](install-fxcop-analyzers.md)portiert wurden, finden Sie unter [Fxcop-Regelportstatus](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Codeanalysewarnungen werden als Fehler behandelt

Wenn Ihr Projekt die Buildoption verwendet, um Warnungen als Fehler zu behandeln, werden FxCop-Analyzerwarnungen möglicherweise als Fehler angezeigt. Um zu verhindern, dass Codeanalysewarnungen als Fehler behandelt werden, führen Sie die Schritte unter [Häufig gestellte Fragen zur Codeanalyse aus.](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über .NET Compiler Platform-Analysetools](roslyn-analyzers-overview.md)
- [Migration zu FxCop-Analysatoren](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Installieren von FxCop-Analysetools](install-fxcop-analyzers.md)
