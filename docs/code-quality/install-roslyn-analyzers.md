---
title: Roslyn-Analyzer in Visual Studio zu installieren | Microsoft Docs
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 0d21b0ab9c5db64c9b5874480c3735bfbb365384
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Installieren von .NET Compiler Platform-Analyzern

Visual Studio-2017 enthält einen Kernsatz von .NET Compiler Platform (*Roslyn*) Analysen. Folgende Analyzer sind immer aktiviert. Sie können zusätzliche Analysen installieren, als NuGet-Pakete oder als Visual Studio-Erweiterungen in *VSIX* Dateien.

## <a name="to-install-nuget-package-analyzers"></a>So installieren Sie die NuGet-Paket-Analyzern

1. [Bestimmen Sie die Version der Analyzer Paket](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) basierend auf Ihrer Version von Visual Studio zu installieren.

1. Installieren Sie das Paket in Visual Studio, verwenden entweder die [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder [Paket-Manager-UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Die Seite "nuget.org" für jedes Paket Analyzer zeigt den Befehl zum Einfügen in die **Package Manager Console**. Es gibt auch eine praktische Schaltfläche den Text in die Zwischenablage kopiert.
   >
   > ![NuGet.org-Seite, die mit der Paket-Manager-Konsole-Befehl](media/nuget-package-manager-command.png)

   Die Assemblys Analyzer installiert sind und angezeigt werden, **Projektmappen-Explorer** unter **Verweise** > **Analysen**.

   ![Analysen für Knoten im Projektmappen-Explorer](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>So installieren Sie die VSIX-Analyzern

1. Wählen Sie in Visual Studio **Tools** > **Erweiterungen und Updates**.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt von herunterladen [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Erweitern Sie **Online** im linken Bereich, und wählen Sie dann **Visual Studio Marketplace**.

1. Geben Sie in das Suchfeld "Codeanalyse", und suchen Sie nach der **Microsoft Code Analysis 2017** Erweiterung.

   ![Codeanalyse für Microsoft-Erweiterung](media/extensions-and-updates-code-analysis.png)

1. Wählen Sie **herunterladen**.

   Die Erweiterung wird heruntergeladen.

1. Wählen Sie **OK** das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio zum Starten der **VSIX-Installationsprogramm**.

   Die **VSIX-Installationsprogramm** Dialogfeld wird geöffnet.

   ![VSIX-Installationsprogramm für die Microsoft-Codeanalyse](media/vsix-installer-code-analysis.png)

1. Wählen Sie **ändern** um die Installation zu starten.

1. Nachdem Sie eine oder zwei Minuten ist die Installation abgeschlossen werden. Wählen Sie **schließen**.

1. Öffnen Sie Visual Studio erneut.

Wenn Sie überprüfen, ob die Erweiterung installiert, aktivieren wird möchten **Tools** > **Erweiterungen und Updates**. In der **Erweiterungen und Updates** wählen Sie im Dialogfeld die **installiert** Kategorie auf der linken Seite, und suchen Sie nach dem Namen für die Erweiterung.

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden Sie Roslyn-Analyzer in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analyzer in Visual Studio](../code-quality/roslyn-analyzers-overview.md)