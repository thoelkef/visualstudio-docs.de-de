---
title: Installieren von Roslyn-Analysetools
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1afeb6f75648ce2ab1687fa9262ab28b658b0d70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820820"
---
# <a name="install-net-compiler-platform-analyzers"></a>Installieren von .NET Compiler Platform-Analysetools

Visual Studio enthält einen Kernsatz von .NET Compiler Platform (*Roslyn*) Analyzer. Diese Analysemodule sind immer aktiviert. Sie können zusätzliche Analysen installieren, entweder als NuGet-Pakete oder als Visual Studio-Erweiterungen in *VSIX* Dateien.

## <a name="to-install-nuget-analyzer-packages"></a>Zum Installieren von Paketen für NuGet-analyzer

1. Suchen Sie das Paket des Analysetools, die, das Sie auf www.nuget.org installieren möchten.

   Beispielsweise möchten [installieren die Microsoft FxCop-Analysetools](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) um den Code auf Sicherheit und Leistung Probleme, u. a. zu überprüfen. Oder installieren Sie [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) nach Problemen in Ihrer Codebasis gesucht werden soll.

2. Installieren Sie das Paket in Visual Studio mit der [-Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder [-Paket-Manager-UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Die Seite www.nuget.org für jedes analyzerpaket erfahren Sie, den Befehl zum Einfügen in die **-Paket-Manager-Konsole**. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.

   Der Analyzer-Assemblys werden installiert und werden in **Projektmappen-Explorer** unter **Verweise** > **Analysen**.

## <a name="to-install-vsix-analyzers"></a>So installieren Sie die VSIX-Analysen

::: moniker range="vs-2017"

1. Wählen Sie in Visual Studio **Tools** > **Erweiterungen und Updates**.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie suchen und Laden Sie die Analyzer-Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten von Erweiterungen**.

   Die **Verwalten von Erweiterungen** Dialogfeld wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie suchen und Laden Sie die Analyzer-Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace**.

3. Geben Sie in das Suchfeld den Namen der Analyzer-Erweiterung, die Sie installieren möchten. Beispielsweise möchten [installieren die Microsoft FxCop-Analysetools](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) um den Code auf Sicherheit und Leistung Probleme, u. a. zu überprüfen.

4. Wählen Sie **herunterladen**.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** , um das Dialogfeld schließen, und schließen Sie alle Instanzen von Visual Studio zum Starten der **VSIX-Installationsprogramm**.

   Die **VSIX-Installationsprogramm** Dialogfeld wird geöffnet.

   ![VSIX-Installationsprogramm für die Microsoft-Codeanalyse](media/vsix-installer-code-analysis.png)

6. Wählen Sie **ändern** um die Installation zu starten.

7. Nach ein oder zwei Minuten ist die Installation abgeschlossen werden. Klicken Sie auf **Schließen**.

8. Öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Sollten Sie überprüfen, ob die Erweiterung installiert, wählen ist **Tools** > **Erweiterungen und Updates**. In der **Erweiterungen und Updates** wählen Sie im Dialogfeld die **installiert** Kategorie auf der linken Seite, und klicken Sie dann für die Erweiterung anhand des Namens suchen.

::: moniker-end

::: moniker range=">=vs-2019"

Sollten Sie überprüfen, ob die Erweiterung installiert, wählen ist **Erweiterungen** > **Verwalten von Erweiterungen**. In der **Verwalten von Erweiterungen** wählen Sie im Dialogfeld die **installiert** Kategorie auf der linken Seite, und suchen Sie nach dem Namen für die Erweiterung.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwenden von Roslyn-Analysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analysetools in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Install FxCop analyzers (Installieren von FxCop-Analysetools)](../code-quality/install-fxcop-analyzers.md)