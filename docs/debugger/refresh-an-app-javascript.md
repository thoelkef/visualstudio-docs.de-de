---
title: "Aktualisieren einer App (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, Aktualisierung von Seiten [Windows Store-Apps]"
  - "DOM-Explorer, Aktualisieren [Windows Store-Apps]"
  - "JavaScript-Debugging, Aktualisierung von Seiten [Windows Store-Apps]"
  - "Aktualisieren [Windows Store-Apps]"
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Aktualisieren einer App (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt für Windows und Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Sie können während des Debuggens Änderungen am Code vornehmen und dann eine mit JavaScript erstellte Store\-App aktualisieren, indem Sie auf der Symbolleiste **Debuggen** die Schaltfläche **Windows\-App aktualisieren** auswählen.  Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten.  Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript\-Code zu ändern und das Ergebnis schnell anzuzeigen.  Dieses Feature wird sowohl für Windows Store\- als auch für Windows Phone Store\-Apps unterstützt.  
  
 Aktualisieren hält weder den App\-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:  
  
-   Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.  
  
-   Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK\-Verweises, oder Änderungen an den Komponenten für Windows\-Runtime \(.winmd\-Dateien\).  
  
-   Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson\-Dateien.  
  
-   Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.  
  
-   Projekt\- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging\-Gerät oder Änderungen an der Paketaktion für eine Datei \(im Eigenschaftenfenster\).  
  
> [!IMPORTANT]
>  Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML\-, CSS\- und JavaScript\-Quelldateien zu aktualisieren.  
  
### So aktualisieren Sie eine App  
  
1.  Erstellen Sie in Visual Studio ein neues Projekt mit der Navigations\-App\-Projektvorlage.  
  
     Dies kann eine Windows Store\-App, eine Windows Phone Store\-App oder eine universelle App sein.  
  
2.  Wählen Sie bei geöffneter Vorlage in Visual Studio ein Debugziel aus.  
  
     Wenn das aktuelle Startprojekt ein Windows Phone\-Projekt ist, wählen Sie einen Windows Phone\-Emulator als Debugziel aus.  Andernfalls wählen Sie **Simulator** oder **Lokaler Computer** aus.  
  
     ![Debug&#45;Zielliste auswählen](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
3.  Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
4.  Wechseln Sie zu Visual Studio.  \(Drücken Sie F12.\)  
  
5.  Öffnen Sie im **Projektmappen\-Explorer** im Ordner **Seiten** \> **Startseite** die Datei „home.html“.  
  
6.  Ändern Sie den Seitentiteltext von  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     in einen Text wie den folgenden:  
  
    ```html  
    Hello!  
    ```  
  
7.  Klicken Sie auf die Schaltfläche **Windows\-App aktualisieren**, die wie folgt aussieht: ![Schaltfläche "Windows&#45;App aktualisieren"](../debugger/media/js_refresh.png "JS\_Refresh").  \(Oder drücken Sie F4\)  
  
8.  Wechseln Sie zur App.  Die App wird erneut geladen, ohne dass der Debugger neu gestartet wird, und der neue Seitentitel wird angezeigt.  
  
## Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)