---
title: Installieren von FxCop-Analysetools
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b5cb0fa5985cbc923713330289d7f83ed1fd954e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551109"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installieren von FxCop-Analyzern in Visual Studio

Microsoft hat eine Reihe von Analyzern namens [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)erstellt, die die wichtigsten "FxCop"-Regeln aus der Legacy Analyse enthalten. Diese Analysen überprüfen den Code unter anderem auf Sicherheits-, Leistungs-und Entwurfs Probleme.

Sie können diese FxCop-Analysen entweder als nuget-Paket oder als VSIX-Erweiterung für Visual Studio installieren. Weitere Informationen zu den vor-und Nachteile finden [Sie unter nuget-Paket im Vergleich zu VSIX-](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)Erweiterung.

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>So installieren Sie FxCop-Analysen als nuget-Paket

1. Bestimmen Sie basierend auf Ihrer Version von Visual Studio, [welche Version des Analyzer-Pakets](#fxcopanalyzers-package-versions) installiert werden muss.

2. Installieren Sie das Paket in Visual Studio, indem Sie entweder die [Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)verwenden.

   > [!NOTE]
   > Die Seite "nuget.org" für jedes Analysepaket zeigt den Befehl an, der in die **Paket-Manager-Konsole**eingefügt werden soll. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.
   >
   > ![NuGet.org Seite mit dem Befehl "Paket-Manager-Konsole"](media/nuget-package-manager-command.png)

   Die Analyzer-Assemblys werden installiert und in **Projektmappen-Explorer** unter **Verweise** > -**Analyzers**angezeigt.

   ![Analyzers-Knoten in Projektmappen-Explorer](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Fxcopanalyzers-Paketversionen

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, welche Version des FxCop-Analysen-Pakets für Ihre Version von Visual Studio installiert werden soll:

| Visual Studio-Version | FxCop Analyzer-Paketversion |
| - | - |
| Visual Studio 2019 (alle Versionen)<br />Visual Studio 2017 Version 15,8 und höher | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017, Version 15,5 bis 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017, Version 15,3 bis 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017, Version 15,0 bis 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 und 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>So installieren Sie FxCop-Analysen als VSIX

::: moniker range="vs-2017"

In Visual Studio 2017, Version 15,5 und höher, können Sie die [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) -Erweiterung installieren, die alle FxCop-Analysen für verwaltete Projekte enthält.

1. Wählen Sie > in Visual Studio Extras **Erweiterungen und Updates**aus.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt von [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)herunterladen.

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace**aus.

3. Geben Sie im Suchfeld "Code Analyse" ein, und suchen Sie nach der Erweiterung **Microsoft Code Analysis 2017** .

   ![Microsoft Code Analysis 2017-Erweiterung](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Die [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) -Erweiterung enthält alle FxCop-Analysen für verwaltete Projekte. So installieren Sie diese Erweiterung:

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten Erweiterungen**aus.

   Das Dialogfeld **Erweiterungen verwalten** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt von [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)herunterladen.

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace**aus.

3. Geben Sie im Suchfeld "Code Analyse" ein, und suchen Sie nach der Erweiterung **Microsoft Code Analysis 2019** .

   ![Microsoft Code Analysis 2019-Erweiterung](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Wählen Sie **herunterladen**.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** aus, um das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio, um das **VSIX-Installations**Programm zu starten.

   Das Dialogfeld **VSIX-Installer** wird geöffnet.

   ::: moniker range="vs-2017"

   ![VSIX-Installer für die Microsoft-Code Analyse](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wählen Sie **ändern** aus, um die Installation zu starten.

   Nach einer oder zwei Minuten wird die Installation abgeschlossen.

7. Wählen Sie **Schließen**aus, und öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, > wählen Sie Extras**Erweiterungen und Updates**aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, klicken Sie auf **Erweiterungen** > **Verwalten Erweiterungen**. Wählen Sie im Dialogfeld **Erweiterungen verwalten** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Code Analysemodulen in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migration von der Legacy Analyse zu Code Analysen](../code-quality/fxcop-analyzers.yml)
