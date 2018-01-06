---
title: Aktualisieren Sie eine universelle Windows-Plattform oder Windows 8.1-App | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 636f88313d53625e5bb778ffe7bebc8f891ed4bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="refresh-a-uwp-or-windows-81-app"></a>Aktualisieren Sie eine universelle Windows-Plattform oder Windows 8.1-App
![Gilt für Windows und Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Sie können Änderungen an Code vornehmen, während Sie Debuggen, und aktualisieren Sie eine uwp-app mit JavaScript durch Auswählen der **Windows-app aktualisieren** auf die Schaltfläche der **Debuggen** Symbolleiste. Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten. Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript-Code zu ändern und das Ergebnis schnell anzuzeigen. Diese Funktion ist für universelle Windows-Plattform und Windows 8.1-apps unterstützt.  
  
 Aktualisieren hält weder den App-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:  
  
-   Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.  
  
-   Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK-Verweises, oder Änderungen an den Komponenten für Windows-Runtime (.winmd-Dateien).  
  
-   Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson-Dateien.  
  
-   Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.  
  
-   Projekt- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging-Gerät oder Änderungen an der Paketaktion für eine Datei (im Eigenschaftenfenster).  
  
> [!IMPORTANT]
>  Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML-, CSS- und JavaScript-Quelldateien zu aktualisieren.  
  
### <a name="to-refresh-an-app"></a>So aktualisieren Sie eine App  
  
1.  Erstellen Sie in Visual Studio ein neues Projekt mit der Navigations-App-Projektvorlage.  
  
     Dies kann uwp-app oder eine Windows 8.1-app sein.  
  
2.  Wählen Sie bei geöffneter Vorlage in Visual Studio ein Debugziel aus.  
  
     Wenn das aktuelle Startprojekt ein Windows Phone-Projekt ist, wählen Sie einen Windows Phone-Emulator als Debugziel aus. Wählen Sie andernfalls **Simulator** oder **lokalen**.  
  
     ![Debugzielliste auswählen](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
4.  Wechseln Sie zu Visual Studio. (Drücken Sie F12.)  
  
5.  In **Projektmappen-Explorer**in der **Seiten** > **home** Ordner, öffnen die Datei "Home.HTML".  
  
6.  Ändern Sie den Seitentiteltext von  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     in einen Text wie den folgenden:  
  
    ```html  
    Hello!  
    ```  
  
7.  Klicken Sie auf die **Windows-app aktualisieren** Schaltfläche, die wie folgt: ![aktualisieren Sie Windows-app-Schaltfläche](../debugger/media/js_refresh.png "JS_Refresh"). (Oder drücken Sie F4)  
  
8.  Wechseln Sie zur App. Die App wird erneut geladen, ohne dass der Debugger neu gestartet wird, und der neue Seitentitel wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)