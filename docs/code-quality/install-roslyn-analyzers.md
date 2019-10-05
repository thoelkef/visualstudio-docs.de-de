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
ms.openlocfilehash: 284f33d9d7af885958ed13101e1449edc5c8f2be
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551091"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Installieren von .NET Compiler Platform Code-Analyzern

Visual Studio enthält einen Kernsatz von .NET Compiler Platform-Analyzers (*Roslyn*). Diese Analysen sind immer eingeschaltet. Sie können zusätzliche Analysen entweder als nuget-Pakete oder als Visual Studio-Erweiterungen in *VSIX* -Dateien installieren.

## <a name="to-install-nuget-analyzer-packages"></a>So installieren Sie nuget Analyzer-Pakete

1. Suchen Sie das Analyzer-Paket, das Sie installieren möchten, auf www.nuget.org.

   Beispielsweise können Sie [die Microsoft FxCop-Analysen installieren](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) , um den Code unter anderem auf Sicherheits-und Leistungsprobleme zu überprüfen. Sie können auch [stylecopanalyzers](https://www.nuget.org/packages/stylecop.analyzers/) installieren, um nach Stil Problemen in Ihrer Codebasis zu suchen.

2. Installieren Sie das Paket in Visual Studio, indem Sie entweder die [Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)verwenden.

   > [!NOTE]
   > Die Seite www.nuget.org für jedes Analysepaket zeigt den Befehl an, der in die **Paket-Manager-Konsole**eingefügt werden soll. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.

   Die Analyzer-Assemblys werden installiert und in **Projektmappen-Explorer** unter **Verweise** > -**Analyzers**angezeigt.

## <a name="to-install-vsix-analyzers"></a>So installieren Sie VSIX-Analysen

::: moniker range="vs-2017"

1. Wählen Sie > in Visual Studio Extras **Erweiterungen und Updates**aus.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Analyseprogramm Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com)suchen und herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten Erweiterungen**aus.

   Das Dialogfeld **Erweiterungen verwalten** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Analyseprogramm Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com)suchen und herunterladen.

::: moniker-end

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace**aus.

3. Geben Sie im Suchfeld den Namen der Analyzer-Erweiterung ein, die Sie installieren möchten. Beispielsweise können Sie [die Microsoft FxCop-Analysen installieren](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) , um den Code unter anderem auf Sicherheits-und Leistungsprobleme zu überprüfen.

4. Wählen Sie **herunterladen**.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** aus, um das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio, um das **VSIX-Installations**Programm zu starten.

   Das Dialogfeld **VSIX-Installer** wird geöffnet.

   ![VSIX-Installer für die Microsoft-Code Analyse](media/vsix-installer-code-analysis.png)

6. Wählen Sie **ändern** aus, um die Installation zu starten.

7. Nach einer oder zwei Minuten wird die Installation abgeschlossen. Klicken Sie auf **Schließen**.

8. Öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, > wählen Sie Extras**Erweiterungen und Updates**aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, klicken Sie auf **Erweiterungen** > **Verwalten Erweiterungen**. Wählen Sie im Dialogfeld **Erweiterungen verwalten** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwenden von Code Analysemodulen in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Install FxCop analyzers (Installieren von FxCop-Analysetools)](../code-quality/install-fxcop-analyzers.md)