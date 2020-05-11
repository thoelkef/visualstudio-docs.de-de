---
title: Installieren von FxCop-Analysetools
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508770"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installieren von FxCop-Analysatoren in Visual Studio

Microsoft hat eine Reihe von Analysatoren namens [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)erstellt, die die wichtigsten "FxCop"-Regeln aus der Legacyanalyse enthält. Diese Analysatoren überprüfen Ihren Code unter anderem auf Sicherheits-, Leistungs- und Entwurfsprobleme.

Sie können diese FxCop-Analysatoren entweder als NuGet-Paket oder als VSIX-Erweiterung für Visual Studio installieren. Weitere Informationen zu den Vor- und Nachteilen der einzelnen Informationen finden Sie unter [NuGet-Paket vs. VSIX-Erweiterung](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>NuGet-Paket

::: moniker range=">=vs-2019"

In Visual Studio 2019 Version 16.3 und höher können Sie das [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet-Paket direkt über die Eigenschaftenseite Codeanalyse des Projekts installieren:

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer**, wählen Sie **Eigenschaften**aus, und wählen Sie dann die Registerkarte **Codeanalyse** aus.

   ![Installieren des FxCop-Analyzers-Pakets von der Eigenschaftenseite in Visual Studio](media/install-fxcop-properties-page.png)

2. Wählen Sie **Installieren** aus.

   Visual Studio installiert die neueste Version des Microsoft.CodeAnalysis.FxCopAnalyzers-Pakets. Die Assemblys werden im **Projektmappen-Explorer** unter > **Referenzen-Analyzer**angezeigt. **References**

   ![Analyzers-Knoten im Projektmappen-Explorer](media/solution-explorer-analyzers-node.png)

Wenn Sie eine ältere Version von Visual Studio 2019 verwenden, installieren Sie das Paket entweder über die [Package Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Package Manager-Benutzeroberfläche](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. Bestimmen Sie basierend auf Ihrer Version von Visual [Studio, welche Analysepaketversion](#fxcopanalyzers-package-versions) installiert werden soll.

2. Installieren Sie das Paket in Visual Studio entweder über die [Package Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Package Manager-Benutzeroberfläche](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Die nuget.org Seite für jedes Analyzerpaket zeigt Ihnen den Befehl zum Einfügen in die **Package Manager Console**an. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.
   >
   > ![NuGet.org Seite mit dem Befehl Package Manager Console](media/nuget-package-manager-command.png)

   Die Analyzerassemblys werden installiert und werden im **Projektmappen-Explorer** unter > **Referenzen-Analyzer**angezeigt. **References**

::: moniker-end

### <a name="custom-installation"></a>Benutzerdefinierte Installation

Wählen Sie für eine benutzerdefinierte Installation, z. B. um eine andere Version des Pakets anzugeben, die Schaltfläche Auslassungspunkte (...) auf der Eigenschaftenseite Codeanalyse des Projekts aus. Mit dieser Schaltfläche wird der NuGet-Paketmanager mit "Microsoft.CodeAnalysis.FxCopAnalyzers" als Suchzeichenfolge geöffnet.

![Installieren sie benutzerdefinierte fxCop-Analyzer-Paket von der Eigenschaftenseite in Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Bestimmen Sie basierend auf Ihrer Version von Visual [Studio, welche Analysepaketversion](#fxcopanalyzers-package-versions) installiert werden soll. Sie können das Paket auch über die [Package Manager-Benutzeroberfläche](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)installieren.

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers-Paketversionen

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, welche Version des FxCop-Analyzers-Pakets für Ihre Version von Visual Studio installiert werden soll:

| Visual Studio-Version | FxCop-Analyzer-Paketversion |
| - | - |
| Visual Studio 2019 (alle Versionen)<br />Visual Studio 2017 Version 15.8 und höher | [Neuesten](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 Version 15.5 bis 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 Version 15.3 bis 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 Version 15.0 bis 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015-Update 2 und 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

In Visual Studio 2017 Version 15.5 und höher können Sie die [Microsoft Code Analysis 2017-Erweiterung](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) installieren, die alle FxCop-Analysatoren für verwaltete Projekte enthält.

1. Wählen Sie in Visual Studio **Tools** > **Extensions and Updates**aus.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt aus [Visual Studio Marketplace herunterladen.](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)

2. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace aus.**

3. Geben Sie im Suchfeld "Codeanalyse" ein, und suchen Sie nach der **Erweiterung Microsoft Code Analysis 2017.**

   ![Microsoft Code Analysis 2017-Erweiterung](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Die [Erweiterung Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) enthält alle FxCop-Analysatoren für verwaltete Projekte. So installieren Sie diese Erweiterung:

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten von Erweiterungen**aus.

   Das Dialogfeld **Erweiterungen verwalten** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt aus [Visual Studio Marketplace herunterladen.](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)

2. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace aus.**

3. Geben Sie im Suchfeld "Codeanalyse" ein, und suchen Sie nach der **Erweiterung Microsoft Code Analysis 2019.**

   ![Microsoft Code Analysis 2019-Erweiterung](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Wählen Sie **Herunterladen**.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** aus, um das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio, um den **VSIX Installer**zu starten.

   Das Dialogfeld **VSIX Installer** wird geöffnet.

   ::: moniker range="vs-2017"

   ![VSIX-Installationsprogramm für Microsoft-Codeanalyse](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wählen Sie **Ändern** aus, um die Installation zu starten.

   Nach ein oder zwei Minuten wird die Installation abgeschlossen.

7. Wählen Sie **Schließen**aus , und öffnen Sie dann Visual Studio erneut.

::: moniker range="vs-2017"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, wählen Sie **Tools** > **Extensions and Updates**aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** die Kategorie **Installiert** auf der linken Seite aus, und suchen Sie dann nach der Erweiterung nach Namen.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, wählen Sie **Erweiterungen** > **Erweiterungen verwalten**aus. Wählen Sie im Dialogfeld **Erweiterungen verwalten** die Kategorie **Installiert** auf der linken Seite aus, und suchen Sie dann nach der Erweiterung nach Namen.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Übersicht der Codeanalysatoren in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migration von Legacy-Analysen zu Codeanalysatoren](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
