---
title: Debuggen eines WebView-Steuerelements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f8a4dcc64903b97e3b469fb962777e3b90f84ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729061"
---
# <a name="debug-a-webview-control"></a>Debuggen eines WebView-Steuerelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt Sie für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "Windows_and_phone_content")  
  
 Um `WebView`-Steuerelemente in einer Windows-Runtime-App zu überprüfen und zu debuggen, können Sie Visual Studio so konfigurieren, dass es den Skriptdebugger anfügt, wenn Sie Ihre App starten. Ab Visual Studio 2013 Update 2 haben Sie zwei Möglichkeiten für die Interaktion mit den `WebView`-Steuerelementen bei Verwendung des Debuggers:  
  
-   Öffnen der [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) für eine `WebView` -Instanz, und Überprüfen von DOM-Elemente, untersuchen Sie CSS-formatvorlagenprobleme und Testen Sie dynamisch gerenderte Änderungen an Formatvorlagen.  
  
-   Wählen Sie die Webseite oder `iFrame` angezeigt, der `WebView` Instanz als Ziel in der [JavaScript-Konsole](../debugger/javascript-console-commands.md) Fenster, und klicken Sie dann die Webseite über Konsolenbefehle interagieren. Die Konsole bietet Zugriff auf den aktuellen Skriptausführungskontext.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Anfügen des Debuggers (C#, Visual Basic, C++)  
  
1.  In Visual Studio: Fügen Sie ein `WebView`-Steuerelement an Ihre Windows-Runtime-App an.  
  
2.  Öffnen Sie im Projektmappen-Explorer die Eigenschaften für das Projekt durch Auswahl **Eigenschaften** aus dem Kontextmenü für das Projekt.  
  
3.  Wählen Sie **Debuggen**. In der **Anwendungsprozess** wählen **Skript**.  
  
     ![Skript-Debugger](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Optional) Deaktivieren der just-in-Time (JIT) Debuggen, indem Sie die Auswahl für nicht-Express-Versionen von Visual Studio, **Tools**, **Optionen**, **Debuggen**, **Just-In-Time-**, und klicken Sie dann deaktivieren von JIT-Debuggen für Skript.  
  
    > [!NOTE]
    >  Indem Sie das JIT-Debuggen deaktivieren, können Sie Dialogfelder für unbehandelte Ausnahmen ausblenden, die auf einigen Webseiten auftreten. In Visual Studio Express ist das JIT-Debuggen stets deaktiviert.  
  
5.  Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Verwenden des DOM Explorers, um ein WebView-Steuerelement zu untersuchen und zu debuggen  
  
1.  (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.  
  
2.  Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.  
  
3.  Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.  
  
4.  Öffnen Sie das DOM Explorer-Fenster für die `WebView` Steuerelement dazu **Debuggen**, **Windows**, **DOM Explorer**, und wählen Sie dann die URL des der `WebView` , die Sie untersuchen möchten.  
  
     ![Öffnen im DOM Explorer](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     Der mit dem `WebView` verknüpfte DOM Explorer erscheint als neue Registerkarte in Visual Studio.  
  
5.  Anzeigen und Ändern von live-DOM-Elemente und CSS-Formatvorlagen, siehe [Debuggen von CSS-Stilen mithilfe von DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Verwenden des JavaScript-Konsolenfensters, um ein WebView-Steuerelement zu untersuchen und zu debuggen  
  
1.  (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.  
  
2.  Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.  
  
3.  Öffnen Sie im JavaScript-Konsolenfenster für den `WebView` Steuerelement dazu **Debuggen**, **Windows**, **JavaScript-Konsole**.  
  
     Das JavaScript-Konsolenfenster wird angezeigt.  
  
4.  Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.  
  
5.  Wählen Sie im Konsolenfenster die Webseite oder ein `iFrame` angezeigt, indem die `WebView` steuern, der **Ziel** Liste.  
  
     ![Auswahl in der JavaScript-Konsolenfenster als Ziel](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Mithilfe der Konsole können Sie jeweils mit einem einzelnen `WebView`, `iFrame`, Freigabe-Vertrag oder Web-Worker interagieren. Jedes Element erfordert eine separate Instanz des Webplattform-Hosts (WWAHost.exe). Sie können jeweils mit einem Host interagieren.  
  
6.  Anzeigen und Ändern von Variablen in Ihrer app aus, oder verwenden Sie Konsolenbefehle, wie in beschrieben [Schnellstart: Debuggen von JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) und [JavaScript-Konsolenbefehle](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)



