---
title: Aktualisieren einer APP (JavaScript) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841074"
---
# <a name="refresh-an-app-javascript"></a>Aktualisieren einer App (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Sie können während des Debuggens Änderungen am Code vornehmen und dann eine Store-App mithilfe von JavaScript aktualisieren, indem Sie auf der Symbolleiste **Debuggen** die Schaltfläche **Windows-APP aktualisieren** auswählen. Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten. Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript-Code zu ändern und das Ergebnis schnell anzuzeigen. Diese Funktion wird sowohl für Windows Store- als auch für Windows Phone Store-Apps unterstützt.  
  
 Aktualisieren hält weder den App-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:  
  
- Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.  
  
- Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK-Verweises, oder Änderungen an den Komponenten für Windows-Runtime (.winmd-Dateien).  
  
- Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson-Dateien.  
  
- Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.  
  
- Projekt- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging-Gerät oder Änderungen an der Paketaktion für eine Datei (im Eigenschaftenfenster).  
  
> [!IMPORTANT]
> Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML-, CSS- und JavaScript-Quelldateien zu aktualisieren.  
  
### <a name="to-refresh-an-app"></a>So aktualisieren Sie eine App  
  
1. Erstellen Sie in Visual Studio ein neues Projekt mit der Navigations-App-Projektvorlage.  
  
     Dies kann eine Windows Store-App, eine Windows Phone Store-App oder eine universelle App sein.  
  
2. Wählen Sie bei geöffneter Vorlage in Visual Studio ein Debugziel aus.  
  
     Wenn das aktuelle Startprojekt ein Windows Phone-Projekt ist, wählen Sie einen Windows Phone-Emulator als Debugziel aus. Andernfalls wählen Sie **Simulator** oder **lokaler Computer**aus.  
  
     ![Debugzielliste auswählen](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
4. Wechseln Sie zu Visual Studio. (Drücken Sie F12.)  
  
5. Öffnen Sie in **Projektmappen-Explorer**im Ordner " **pages**  >  **Home** " home.html.  
  
6. Ändern Sie den Seitentiteltext von  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     in einen Text wie den folgenden:  
  
    ```html  
    Hello!  
    ```  
  
7. Klicken Sie auf die Schaltfläche **Windows-App aktualisieren**, die wie folgt aussieht: ![Schaltfläche „Windows-App aktualisieren“](../debugger/media/js-refresh.png "JS_Refresh"). (Oder drücken Sie F4)  
  
8. Wechseln Sie zur App. Die App wird erneut geladen, ohne dass der Debugger neu gestartet wird, und der neue Seitentitel wird angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)
