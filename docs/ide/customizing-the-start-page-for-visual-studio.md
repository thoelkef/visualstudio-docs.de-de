---
title: "Anpassen der Startseite für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Anpassen der Startseite für Visual Studio
Sie können die Visual Studio-Startseite standardmäßig auf unterschiedliche Weise anpassen. Sie können das Dialogfeld **Projekt öffnen** anzeigen, oder Sie können die Projektmappe öffnen, die zuletzt geladen wurde. Sie können eine benutzerdefinierte Startseite anzeigen. Dies ist eine Windows Presentation Foundation (WPF)-XAML-Seite, die in einem Toolfenster ausgeführt wird und Visual Studio-interne Befehle ausführen kann.  

## <a name="customize-the-default-start-page"></a>Anpassen der Standardstartseite  

1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  

2.  Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.  

3.  Wählen Sie in der Liste **Beim Start** das gewünschte Element für die Anpassung aus.  

## <a name="show-a-custom-start-page"></a>Anzeigen einer benutzerdefinierten Startseite  

1.  Installieren Sie eine benutzerdefinierte Startseite mit einer der folgenden Methoden:  

    -   Installieren Sie sie über [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), von einer anderen Website oder einer Seite im lokalen Intranet.  

        Öffnen Sie eine VSIX-Datei, die eine benutzerdefinierte Startseite enthält, oder kopieren Sie die Startseitendateien und fügen Sie sie auf dem Computer in den Ordner **%USERPROFILE%\Eigene Dateien\Visual Studio 2017\StartPages** ein.  

    -   Erstellen Sie eine eigene Startseite, wenn Sie Visual Studio SDK installiert haben.  

         Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).  

2.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  

3.  Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.  

4.  Wählen Sie in der Liste **Startseite anpassen** die gewünschte Seite aus.  

> [!NOTE]
>  Wenn ein Fehler in einer benutzerdefinierten Startseite Visual Studio zum Absturz bringt, können Sie Visual Studio im abgesicherten Modus starten und dann festlegen, dass die Standardstartseite verwendet wird. Weitere Informationen finden Sie unter [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Siehe auch  
 [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md)   
