---
title: Debuggen eines WebView-Steuerelements (UWP) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: d55023b97397fa7d1b134c246c25b0d0b37a4d18
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790107"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Debuggen eines WebView-Steuerelements in einer UWP-App

 Um `WebView`-Steuerelemente in einer Windows-Runtime-App zu überprüfen und zu debuggen, können Sie Visual Studio so konfigurieren, dass es den Skriptdebugger anfügt, wenn Sie Ihre App starten. Sie haben zwei Möglichkeiten für die Interaktion mit `WebView` steuert, mit dem Debugger:

-   Öffnen Sie [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) für eine `WebView`-Instanz, und prüfen Sie DOM-Elemente, untersuchen Sie CSS-Formatvorlagenprobleme und testen Sie dynamisch gerenderte Änderungen an Formatvorlagen.

-   Wählen Sie die Webseite oder den `iFrame`, die in der `WebView`-Instanz angezeigt werden, als Ziel im [JavaScript-Konsolenfenster](../debugger/javascript-console-commands.md), und interagieren Sie dann über Konsolenbefehle mit der Webseite. Die Konsole bietet Zugriff auf den aktuellen Skriptausführungskontext.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Anfügen des Debuggers (C#, Visual Basic, C++)

1.  In Visual Studio: Fügen Sie ein `WebView`-Steuerelement an Ihre Windows-Runtime-App an.

2.  Im Projektmappen-Explorer: Öffnen Sie die Eigenschaften für das Projekt, indem Sie im Kontextmenü die Option **Eigenschaften** auswählen.

3.  Wählen Sie **Debuggen** aus. Wählen Sie in der Liste **Anwendungsprozesse** die Option **Skript**.

     ![Skript-Debugger](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4.  (Optional) Für Nicht-Express-Versionen von Visual Studio: Deaktivieren Sie das Just-in-time-Debuggen (JIT), indem Sie **Extras > Optionen > Debuggen > Just-In-Time** auswählen und dann das JIT-Debuggen für Skript deaktivieren.

    > [!NOTE]
    >  Indem Sie das JIT-Debuggen deaktivieren, können Sie Dialogfelder für unbehandelte Ausnahmen ausblenden, die auf einigen Webseiten auftreten. In Visual Studio Express ist das JIT-Debuggen stets deaktiviert.

5.  Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Verwenden des DOM Explorers, um ein WebView-Steuerelement zu untersuchen und zu debuggen

1.  (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.

2.  Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.

3.  Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.

4.  Öffnen Sie das DOM Explorer-Fenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **DOM Explorer** und dann die URL des zu untersuchenden `WebView`-Elements auswählen.

     ![Öffnen im DOM Explorer](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     Der mit dem `WebView` verknüpfte DOM Explorer erscheint als neue Registerkarte in Visual Studio.

5.  Anzeigen und Ändern von live-DOM-Elemente und CSS-Formatvorlagen, siehe [Debuggen von CSS-Stilen mithilfe von DOM Explorer](/visualstudio/debugger/quickstart-debug-html-and-css).

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Verwenden des JavaScript-Konsolenfensters, um ein WebView-Steuerelement zu untersuchen und zu debuggen

1.  (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.

2.  Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.

3.  Öffnen Sie das JavaScript-Konsolenfenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **JavaScript-Konsole** auswählen.

     Das JavaScript-Konsolenfenster wird angezeigt.

4.  Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.

5.  Wählen Sie im Konsolenfenster die Webseite oder einen `iFrame`, der durch das `WebView`-Steuerelement in der Liste **Ziele** angezeigt wird.

     ![Auswahl in der JavaScript-Konsolenfenster als Ziel](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    >  Mithilfe der Konsole können Sie jeweils mit einem einzelnen `WebView`, `iFrame`, Freigabe-Vertrag oder Web-Worker interagieren. Jedes Element erfordert eine separate Instanz des Webplattform-Hosts (WWAHost.exe). Sie können jeweils mit einem Host interagieren.

6.  Anzeigen und Ändern von Variablen in Ihrer app aus, oder verwenden Sie Konsolenbefehle, wie in beschrieben [Schnellstart: Debuggen von JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) und [JavaScript-Konsolenbefehle](../debugger/javascript-console-commands.md).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)