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
ms.openlocfilehash: 9e2fc29723f66fce0fda72a9af1fe40888bd2ce3
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820638"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installieren von FxCop-Analysen in Visual Studio

Microsoft erstellt einen Satz von Analysen, die Namen [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), die Regeln für die wichtigsten "FxCop" aus der Analyse von statischem Code, in der Roslyn-Analysetools konvertiert enthält. Diese Analysetools überprüfen Sie Ihren Code für Aspekte, unter anderem, Sicherheit und Leistung.

Sie können diese FxCop-Analysetools entweder als NuGet-Paket oder als VSIX-Erweiterung für Visual Studio installieren. Über die vor- und Nachteile der einzelnen finden Sie unter [Visual Studio NuGet-Paket. VSIX-Erweiterung](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>FxCop-Analyzer als NuGet-Paket installieren

1. [Bestimmen, welche Version der Analyzer Paket](#fxcopanalyzers-package-versions) basierend auf Ihrer Version von Visual Studio zu installieren.

2. Installieren Sie das Paket in Visual Studio mit der [-Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder [-Paket-Manager-UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Die Seite "NuGet.org" für jedes analyzerpaket erfahren Sie, den Befehl zum Einfügen in die **-Paket-Manager-Konsole**. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.
   >
   > ![NuGet.org-Seite, die mit der Paket-Manager-Konsole](media/nuget-package-manager-command.png)

   Die analysetoolassemblys installiert sind und sie werden in **Projektmappen-Explorer** unter **Verweise** > **Analysen**.

   ![Knoten "Analyzer" im Projektmappen-Explorer](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Aggregierte FxCopAnalyzers-Paketversionen

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, welche Version des Pakets die FxCop-Analysen für Ihre Version von Visual Studio zu installieren:

| Visual Studio-Version | FxCop-Analyse-Paketversion |
| - | - |
| Visual Studio 2019 (alle Versionen)<br />Visual Studio 2017 Version 15,8 und höher | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017 Version 15.5 zu 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 Version 15.3, Version 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 Version 15.0 an 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 und 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Zum Installieren von FxCop-Analyzer als einer VSIX-Datei

::: moniker range="vs-2017"

Sie können auf Visual Studio 2017 Version 15.5 und höher installieren die [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) -Erweiterung, die alle die FxCop-Analysetools für verwaltete Projekte enthält.

1. Wählen Sie in Visual Studio **Tools** > **Erweiterungen und Updates**.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Laden Sie alternativ die Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace**.

3. Geben Sie in das Suchfeld "Codeanalyse" aus, und suchen Sie nach der **Microsoft Code Analysis 2017** Erweiterung.

   ![Microsoft Code Analysis-2017-Erweiterung](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Die [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) Erweiterung enthält alle von der FxCop-Analysen für verwalteten Projekten. Diese Erweiterung zu installieren:

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten von Erweiterungen**.

   Die **Verwalten von Erweiterungen** Dialogfeld wird geöffnet.

   > [!NOTE]
   > Laden Sie alternativ die Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace**.

3. Geben Sie in das Suchfeld "Codeanalyse" aus, und suchen Sie nach der **Microsoft Code Analysis 2019** Erweiterung.

   ![Microsoft Code Analysis 2019-Erweiterung](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Wählen Sie **herunterladen**.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** , um das Dialogfeld schließen, und schließen Sie alle Instanzen von Visual Studio zum Starten der **VSIX-Installationsprogramm**.

   Die **VSIX-Installationsprogramm** Dialogfeld wird geöffnet.

   ::: moniker range="vs-2017"

   ![VSIX-Installationsprogramm für die Microsoft-Codeanalyse](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wählen Sie **ändern** um die Installation zu starten.

   Nach ein oder zwei Minuten ist die Installation abgeschlossen werden.

7. Wählen Sie **schließen**, öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Sollten Sie überprüfen, ob die Erweiterung installiert, wählen ist **Tools** > **Erweiterungen und Updates**. In der **Erweiterungen und Updates** wählen Sie im Dialogfeld die **installiert** Kategorie auf der linken Seite, und klicken Sie dann für die Erweiterung anhand des Namens suchen.

::: moniker-end

::: moniker range=">=vs-2019"

Sollten Sie überprüfen, ob die Erweiterung installiert, wählen ist **Erweiterungen** > **Verwalten von Erweiterungen**. In der **Verwalten von Erweiterungen** wählen Sie im Dialogfeld die **installiert** Kategorie auf der linken Seite, und suchen Sie nach dem Namen für die Erweiterung.

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analysetools in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Roslyn-Analysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrieren von FxCop zu Roslyn-Analysetools](../code-quality/fxcop-analyzers.yml)
