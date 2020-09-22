---
title: Debuggen eines WebView-Steuer Elements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841147"
---
# <a name="debug-a-webview-control"></a>Debuggen eines WebView-Steuerelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Um `WebView`-Steuerelemente in einer Windows-Runtime-App zu überprüfen und zu debuggen, können Sie Visual Studio so konfigurieren, dass es den Skriptdebugger anfügt, wenn Sie Ihre App starten. Ab Visual Studio 2013 Update 2 haben Sie zwei Möglichkeiten für die Interaktion mit den `WebView`-Steuerelementen bei Verwendung des Debuggers:  
  
- Öffnen Sie [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) für eine `WebView`-Instanz, und prüfen Sie DOM-Elemente, untersuchen Sie CSS-Formatvorlagenprobleme und testen Sie dynamisch gerenderte Änderungen an Formatvorlagen.  
  
- Wählen Sie die Webseite oder den `iFrame`, die in der `WebView`-Instanz angezeigt werden, als Ziel im [JavaScript-Konsolenfenster](../debugger/javascript-console-commands.md), und interagieren Sie dann über Konsolenbefehle mit der Webseite. Die Konsole bietet Zugriff auf den aktuellen Skriptausführungskontext.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Anfügen des Debuggers (C#, Visual Basic, C++)  
  
1. In Visual Studio: Fügen Sie ein `WebView`-Steuerelement an Ihre Windows-Runtime-App an.  
  
2. Im Projektmappen-Explorer: Öffnen Sie die Eigenschaften für das Projekt, indem Sie im Kontextmenü die Option **Eigenschaften** auswählen.  
  
3. Wählen Sie **Debuggen** aus. Wählen Sie in der Liste **Anwendungsprozesse** die Option **Skript**.  
  
     ![Anfügen des Skriptdebuggers](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Optionale Deaktivieren Sie für nicht-Express-Versionen von Visual Studio das Just-in-time (JIT)-Debuggen, indem Sie **Tools**, **Optionen**, **Debuggen**, **Just-in-Time**und dann Deaktivierung des JIT-Debuggens für Skripts auswählen.  
  
    > [!NOTE]
    > Indem Sie das JIT-Debuggen deaktivieren, können Sie Dialogfelder für unbehandelte Ausnahmen ausblenden, die auf einigen Webseiten auftreten. In Visual Studio Express ist das JIT-Debuggen stets deaktiviert.  
  
5. Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Verwenden des DOM Explorers, um ein WebView-Steuerelement zu untersuchen und zu debuggen  
  
1. (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.  
  
2. Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.  
  
3. Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.  
  
4. Öffnen Sie das DOM Explorer-Fenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **DOM Explorer** und dann die URL des zu untersuchenden `WebView`-Elements auswählen.  
  
     ![Öffnen von DOM Explorer](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     Der mit dem `WebView` verknüpfte DOM Explorer erscheint als neue Registerkarte in Visual Studio.  
  
5. Zeigen Sie Live-DOM-Elemente und CSS-Formatvorlagen an, und ändern Sie diese wie unter [Debuggen von HTML und CSS in UWP-Apps in Visual Studio](../debugger/debug-css-styles-using-dom-explorer.md) beschrieben.  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Verwenden des JavaScript-Konsolenfensters, um ein WebView-Steuerelement zu untersuchen und zu debuggen  
  
1. (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.  
  
2. Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.  
  
3. Öffnen Sie das JavaScript-Konsolenfenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **JavaScript-Konsole** auswählen.  
  
     Das JavaScript-Konsolenfenster wird angezeigt.  
  
4. Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.  
  
5. Wählen Sie im Konsolenfenster die Webseite oder einen `iFrame`, der durch das `WebView`-Steuerelement in der Liste **Ziele** angezeigt wird.  
  
     ![Zielauswahl im JavaScript-Konsolenfenster](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > Mithilfe der Konsole können Sie jeweils mit einem einzelnen `WebView`, `iFrame`, Freigabe-Vertrag oder Web-Worker interagieren. Jedes Element erfordert eine separate Instanz des Webplattform-Hosts (WWAHost.exe). Sie können jeweils mit einem Host interagieren.  
  
6. Zeigen Sie Variablen in Ihrer App an, und ändern Sie diese, oder verwenden Sie Konsolenbefehle. Dies wird beschrieben unter [Debuggen von JavaScript mithilfe der Konsole in Visual Studio](../debugger/quickstart-debug-javascript-using-the-console.md) und [JavaScript-Konsolenbefehle in Visual Studio](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)
