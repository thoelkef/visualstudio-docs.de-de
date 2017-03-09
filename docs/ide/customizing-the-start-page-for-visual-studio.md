---
title: "Anpassen der Startseite f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.startpage"
  - "VS.StartPage.HowDoI"
  - "vs.ToolsOptionsPages.Startup"
helpviewer_keywords: 
  - "Anpassen der Startseite [Visual Studio]"
  - "Startseite [Visual Studio]"
  - "Visual Studio-Startseite"
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
caps.handback.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Anpassen der Startseite f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Visual Studio\-Startseite standardmäßig auf unterschiedliche Weise anpassen. Sie können das Dialogfeld **Projekt öffnen** anzeigen, oder Sie können die Projektmappe öffnen, die zuletzt geladen wurde.  Sie können eine benutzerdefinierte Startseite anzeigen. Dies ist eine Windows Presentation Foundation \(WPF\)\-XAML\-Seite, die in einem Toolfenster ausgeführt wird und Visual Studio\-interne Befehle ausführen kann.  
  
## Anpassen der Standardstartseite  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  Erweitern Sie **Umgebung**, und wählen Sie dann **Start**.  
  
3.  Wählen Sie in der Liste **Beim Start** das gewünschte Element für die Anpassung aus.  
  
## Anzeigen einer benutzerdefinierten Startseite  
  
1.  Installieren Sie eine benutzerdefinierte Startseite mit einer der folgenden Methoden:  
  
    -   Installieren Sie diese über die [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), eine andere Website oder eine Seite im lokalen Intranet.  
  
        > [!NOTE]
        >  Wenn Sie eine Seite installieren möchten, die für eine frühere Version von Visual Studio verwendet wird, können Sie die Seite mit Visual Studio SDK aktualisieren.  Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren einer benutzerdefinierten Visual Studio\-Startseite](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Öffnen Sie eine VSIX\-Datei, die eine benutzerdefinierte Startseite enthält, oder kopieren Sie die Startseitendateien und fügen Sie sie auf dem Computer in den Ordner „%USERPROFILE%\\Eigene Dateien\\Visual Studio 2015\\StartPages“ ein.  
  
    -   Erstellen Sie eine eigene Startseite, wenn Sie Visual Studio SDK installiert haben.  
  
         Weitere Informationen finden Sie unter [Erstellen einer eigenen Startseite](../misc/creating-your-own-start-page.md).  
  
2.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
3.  Erweitern Sie **Umgebung**, und wählen Sie dann **Start**.  
  
4.  Wählen Sie in der Liste **Startseite anpassen** die gewünschte Seite aus.  
  
> [!NOTE]
>  Wenn ein Fehler in einer benutzerdefinierten Startseite Visual Studio zum Absturz bringt, können Sie Visual Studio im abgesicherten Modus starten und dann festlegen, dass die Standardstartseite verwendet wird.  Weitere Informationen finden Sie unter [\/SafeMode](../ide/reference/safemode-devenv-exe.md).  
  
## Siehe auch  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Erstellen einer eigenen Startseite](../misc/creating-your-own-start-page.md)