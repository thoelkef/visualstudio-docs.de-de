---
title: Installieren einer benutzerdefinierten Startseite oder Ändern des Startelements in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9863fdfbfb73e49d0539ba1060f1e1c56888599c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="customize-the-start-page-for-visual-studio"></a>Anpassen der Startseite für Visual Studio

Sie können die Visual Studio-Startbenutzeroberfläche auf unterschiedliche Weise anpassen. Sie können das Dialogfeld **Projekt öffnen** anzeigen, oder Sie können die Projektmappe öffnen, die zuletzt geladen wurde. Sie können eine benutzerdefinierte Startseite anzeigen. Dies ist eine Windows Presentation Foundation (WPF)-XAML-Seite, die in einem Toolfenster ausgeführt wird und Visual Studio-interne Befehle ausführen kann.

## <a name="to-change-the-startup-item"></a>So ändern Sie das Startelement

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

1. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

1. Wählen Sie in der Liste **Beim Starten** das Element aus, das nach dem Start von Visual Studio angezeigt werden soll.

## <a name="to-show-a-custom-start-page"></a>So zeigen Sie eine benutzerdefinierte Startseite an

Sie können [eine eigene benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) mit dem Visual Studio SDK erstellen oder eine Startseite verwenden, die bereits von einem anderen Benutzer erstellt wurde. Sie finden benutzerdefinierte Startseiten z.B. in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Öffnen Sie zum Installieren einer benutzerdefinierten Startseite eine *VSIX-Datei*, oder kopieren Sie die Startseitendateien, und fügen Sie sie auf dem Computer in den Ordner *%USERPROFILE%\Dokumente\Visual Studio 2017\StartPages* ein.

### <a name="to-select-which-custom-start-page-to-display"></a>So wählen Sie aus, welche benutzerdefinierte Startseite angezeigt werden soll

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

1. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

1. Wählen Sie in der Liste **Startseite anpassen** die gewünschte Seite aus.

> [!NOTE]
> Wenn ein Fehler in einer benutzerdefinierten Startseite Visual Studio zum Absturz bringt, können Sie Visual Studio im abgesicherten Modus starten und dann festlegen, dass die Standardstartseite verwendet wird. Weitere Informationen finden Sie unter [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Siehe auch

[Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md)
