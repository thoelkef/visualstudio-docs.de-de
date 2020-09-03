---
title: Anpassen der Startseite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665852"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Anpassen der Startseite für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Visual Studio-Startseite standardmäßig auf unterschiedliche Weise anpassen. Sie können das Dialogfeld **Projekt öffnen** anzeigen, oder Sie können die Projektmappe öffnen, die zuletzt geladen wurde. Sie können eine benutzerdefinierte Startseite anzeigen. Dies ist eine Windows Presentation Foundation (WPF)-XAML-Seite, die in einem Toolfenster ausgeführt wird und Visual Studio-interne Befehle ausführen kann.

## <a name="customizing-the-default-start-page"></a>Anpassen der Standardstartseite

1. **Wählen Sie**in der Menüleiste Extras, **Optionen**aus.

2. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

3. Wählen Sie in der Liste** Beim Start** das gewünschte Element für die Anpassung aus.

## <a name="show-a-custom-start-page"></a>Anzeigen einer benutzerdefinierten Startseite

1. Installieren Sie eine benutzerdefinierte Startseite mit einer der folgenden Methoden:

    - Installieren Sie sie über [Visual Studio Marketplace](https://marketplace.visualstudio.com/), von einer anderen Website oder einer Seite im lokalen Intranet.

        > [!NOTE]
        > Wenn Sie eine Seite installieren möchten, die für eine frühere Version von Visual Studio verwendet wird, können Sie die Seite mit Visual Studio SDK aktualisieren. Weitere Informationen finden Sie unter [How to: Upgrade a Visual Studio Custom Start Page (Vorgehensweise: Durchführen eines Upgrades für eine benutzerdefinierte Visual Studio-Startseite)](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Öffnen Sie eine VSIX-Datei, die eine benutzerdefinierte Startseite enthält, oder kopieren Sie die Startseitendateien und fügen Sie sie auf dem Computer in den Ordner **%USERPROFILE%\Eigene Dateien\Visual Studio 2015\StartPages** ein.

    - Erstellen Sie eine eigene Startseite, wenn Sie Visual Studio SDK installiert haben.

         Weitere Informationen finden Sie unter [Erstellen einer eigenen Startseite](../misc/creating-your-own-start-page.md).

2. **Wählen Sie**in der Menüleiste Extras, **Optionen**aus.

3. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

4. Wählen Sie in der Liste **Startseite anpassen** die gewünschte Seite aus.

> [!NOTE]
> Wenn ein Fehler in einer benutzerdefinierten Startseite Visual Studio zum Absturz bringt, können Sie Visual Studio im abgesicherten Modus starten und dann festlegen, dass die Standardstartseite verwendet wird. Weitere Informationen finden Sie unter [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Weitere Informationen
 [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Erstellen einer eigenen Startseite](../misc/creating-your-own-start-page.md)
