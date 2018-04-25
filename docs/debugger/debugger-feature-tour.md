---
title: Debugger-Featuretour – Visual Studio | Microsoft Docs
description: Tour zu Visual Studio-debugger
ms.custom: mvc
ms.date: 03/27/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb84fbfa4b8916b963f3f3cc35e044593c5a47e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-debugger"></a>Schnellstart: Uns zunächst an den Visual Studio-Debugger

In diesem Thema werden die Funktionen von Visual Studio-Debugger vorgestellt. Wenn Sie nachvollziehen, die durch Ihre eigene app in Visual Studio öffnen möchten, können Sie dies tun, oder Sie zusammen mit einem Beispiel-app mithilfe führen der [Einsteigerhandbuch](../debugger/getting-started-with-the-debugger.md).

Die hier beschriebenen Funktionen gelten für c#, C++, Visual Basic, JavaScript und anderen Sprachen, die von Visual Studio unterstützt (falls nicht anders) zur Verfügung.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

Zum Debuggen, müssen Sie Ihre app mit dem an den app-Prozess angefügten Debugger zu starten. F5 (**Debuggen > Debuggen starten**) ist die gängigste Methode, um dies vorzunehmen. Aber rechts, nachdem Sie alle Haltepunkte, überprüfen Sie Ihre app nicht festgelegt haben möglicherweise der code, damit wir führen Sie als erstes und dann starten Sie das Debuggen.

Wenn Sie eine Datei im Code-Editor geöffnet haben, können Sie einen Haltepunkt festlegen, indem Sie auf den Rand links neben einer Codezeile.

![Festlegen eines Haltepunkts](../debugger/media/dbg-tour-set-a-breakpoint.gif "Festlegen eines Haltepunkts")

Drücken Sie F5 (**Debuggen > Debuggen starten**) und der Debugger ausgeführt wird, bis zum ersten Breakpoint aus, die er erkennt. Wenn die app noch nicht ausgeführt wird, wird F5 wird der Debugger gestartet und hält bei der erste Haltepunkt.

Haltepunkte sind nützlich, wenn Sie wissen, die Zeile des Codes oder Abschnitt des Codes, die Sie im Detail untersuchen möchten.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren Sie im Code im Debugger mit Schritt-Befehlen

Wir stellen die Tastenkombinationen für die meisten Befehle bereit, da sie Navigation in den app-Code beschleunigen. (Entspricht Befehle z. B. Menübefehle in Klammern angezeigt werden.)

Drücken Sie F11, um Ihre app mit dem angefügten Debugger zu starten (**Debuggen > Einzelschritt**). F11 ist die **Einzelschritt** Befehl und setzt die app Ausführung einer Anweisung zu einem Zeitpunkt. Wenn Sie die app mit F11 beginnen, unterbricht der Debugger bei der ersten Anweisung, die ausgeführt wird.

![F11 Einzelschritt](../debugger/media/dbg-tour-f11.png "F11 Einzelschritt")

Der gelbe Pfeil stellt die Anweisung auf der der Debugger angehalten, die auch app-Ausführung an der gleichen Stelle unterbricht (diese Anweisung wurde noch nicht ausgeführt).

F11 ist eine gute Möglichkeit, die den Ausführungsfluss in den meisten Details zu überprüfen. (Um den Code schneller zu durchlaufen, erfahren Sie einige andere Optionen sowie.) Standardmäßig überspringt der Debugger Nichtbenutzercode (Wenn Sie mehr Details anzeigen möchten, finden Sie unter [nur mein Code](../debugger/just-my-code.md)).

>[!NOTE]
> In verwaltetem Code sehen Sie ein Dialogfeld gefragt, ob Sie benachrichtigt werden, wenn Sie automatisch Eigenschaften und Operatoren (Standardverhalten) überspringen möchten. Wenn Sie die Einstellung ändern möchten höher deaktivieren **Eigenschaften und Operatoren überspringen** festlegen in der **Tools > Optionen** Menü unter **Debuggen**.

## <a name="step-over-code-to-skip-functions"></a>Prozedurschritt für Code, um Funktionen zu überspringen.

Wenn Sie in einer Zeile des Codes, die Aufruf einer Funktion oder Methode ist sind, drücken Sie F10 (**Debuggen > Prozedurschritt**) anstelle von F11.

F10 setzt des Debuggers, ohne die schrittweise Ausführung von Funktionen oder Methoden in Ihrem app-Code (der Code wird noch ausgeführt). Durch Drücken der Taste F10, können Sie über Code überspringen, denen Sie nicht interessiert sind. Auf diese Weise können schnell Code abrufen, denen Sie mehr interessiert sind.

## <a name="step-into-a-property"></a>Einzelschritt in eine Eigenschaft

Erwähnt, wird standardmäßig der Debugger überspringt aus verwalteten Eigenschaften und Felder, aber die **Schritt in bestimmten** Befehl können Sie dieses Verhalten außer Kraft setzen.

Mit der rechten Maustaste auf eine Eigenschaft oder ein Feld, und wählen Sie **Schritt in bestimmten**, wählen Sie dann eine der verfügbaren Optionen.

![Einzelschritt in die spezifische](../debugger/media/dbg-tour-step-into-specific.png "Einzelschritt spezifische")

In diesem Beispiel **Schritt in bestimmten** ruft Sie uns auf den Code für `Path.set`.

![Einzelschritt in die spezifische](../debugger/media/dbg-tour-step-into-specific-2.png "Einzelschritt spezifische")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Führen Sie auf einen Punkt im Code schnell mit der Maus

Im Debugger, zeigen Sie auf eine Codezeile, bis die **ausführen, klicken Sie auf** (Ausführung hier)-Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick") auf der linken Seite angezeigt wird.

![Klicken Sie auf Ausführen](../debugger/media/dbg-tour-run-to-click-2.png "ausführen, klicken Sie auf")

>  [!NOTE] 
> Die **ausführen, klicken Sie auf** (Ausführung hier)-Schaltfläche ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Klicken Sie auf die **ausführen, klicken Sie auf** (Ausführung hier)-Schaltfläche. Der Debugger setzt die Codezeile, auf Sie geklickt.

Mit dieser Schaltfläche ähnelt der einen temporären Haltepunkt festlegen. Dieser Befehl ist auch nützlich für die schnelle Umgehung innerhalb eines sichtbaren Bereichs des app-Code. Sie können **Ausführen bis auf** in einer geöffneten Datei.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Wechseln Sie den Debugger, Rücksprung aus der aktuellen Funktion

In manchen Fällen empfiehlt es sich um die Debugsitzung fortsetzen, aber den Debugger über die aktuelle Funktion bis hin zu gelangen.

Drücken Sie UMSCHALT + F11 (oder **Debuggen > Ausführen bis Rücksprung**).

Dieser Befehl setzt die app-Ausführung (und den Debugger setzt) bis die aktuelle Funktion zurückgibt.

## <a name="run-to-cursor"></a>Ausführen bis Cursor

Beenden Sie den Debugger durch Drücken der **Beenden des Debuggens** rote Schaltfläche ![Beenden des Debuggens](../debugger/media/dbg-tour-stop-debugging.png "Beenden des Debuggens") oder UMSCHALT + F5.

Mit der rechten Maustaste einer Codezeile in der app, und wählen Sie **Ausführen bis Cursor**. Dieser Befehl startet das Debuggen und legt einen temporären Haltepunkt in der aktuellen Zeile des Codes.

![Ausführen bis Cursor](../debugger/media/dbg-tour-run-to-cursor.png "Ausführen bis Cursor")

Wenn Sie die Breakpoints festgelegt haben, hält der Debugger für den ersten Haltepunkt, den es trifft.

Drücken Sie F5, bis Sie die Codezeile erreichen, in dem ausgewählten **Ausführen bis Cursor**.

Dieser Befehl ist nützlich, wenn Sie Code bearbeiten und schnell einen temporären Haltepunkt festlegen und den Debugger starten möchten.


> [!NOTE]
> Sie können **Ausführen bis Cursor** in der **Aufrufliste** Fenster, die während des Debuggens.

## <a name="restart-your-app-quickly"></a>Die app schnell neu startet

Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "App neu starten") auf der Debug-Symbolleiste (**STRG + UMSCHALT + F5**).

Wenn Sie drücken **Neustart**, es sparen Sie Zeit und Beenden der app und der Debugger neu gestartet. Der Debugger hält am ersten Haltepunkt, der erreicht wird, indem Sie Code ausführen.

Wenn Sie den Debugger beenden und wieder in den Codeeditor abrufen möchten, können Sie zum Beenden der rote drücken ![Beenden des Debuggens](../debugger/media/dbg-tour-stop-debugging.png "Beenden des Debuggens") anstelle der Schaltfläche **Neustart**.

## <a name="inspect-variables-with-data-tips"></a>Überprüfung von Variablen mit Datentipps

Nun, dass Sie Ihre etwas vertraut sind, müssen Sie eine gute Gelegenheit handelt, überprüfen den app-Zustand (Variablen) mit dem Debugger starten. Funktionen, die Ihnen ermöglichen, Variablen zu überprüfen sind einige der nützlichsten Funktionen des Debuggers, und es gibt verschiedene Möglichkeiten zu diesem Zweck. Häufig, wenn Sie versuchen, ein Problem debuggen können, versuchen Sie, herauszufinden, ob Variablen die Werte, die sie in einer bestimmten app-Status haben voraussichtlich gespeichert sind.

Während im Debugger angehalten wird, zeigen Sie auf ein Objekt mit der Maus, und Sie sehen, dass der Standardwert der Eigenschaft (in diesem Beispiel wird der Dateiname `market 031.jpg` ist der Standardwert der Eigenschaft).

![Anzeigen von einem Datentipp](../debugger/media/dbg-tour-data-tips.gif "einen Datentipp anzeigen")

Erweitern Sie das Objekt, um alle seine Eigenschaften anzuzeigen (z. B. die `FullPath` Eigenschaft in diesem Beispiel).

Häufig beim Debuggen, möchten Sie eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte, und die Datentipps sind eine gute Möglichkeit zu diesem Zweck.

> [!TIP]
> In den meisten unterstützten Sprachen können Sie Code in der Mitte einer Debugsitzung bearbeiten. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Überprüfung von Variablen mit den Fenstern "Auto" und "lokal"

Während des Debuggens, sehen Sie sich die **"Auto"** -Fensters am unteren Rand der Code-Editor.

![Fenster Fenster Auto](../debugger/media/dbg-tour-autos-window.png "Fenster "Auto"")

In der **"Auto"** Fenster finden Sie unter Variablen zusammen mit ihren aktuellen Wert und Typ. Die **"Auto"** Fenster enthält alle Variablen, die in der aktuellen Zeile oder die vorangehende Zeile verwendet wird (In C++ wird das Fenster zeigt Variablen in der vorhergehenden drei Codezeilen. In der Dokumentation für die sprachspezifisches Verhalten).

> [!NOTE]
> In JavaScript die **"lokal"** Fenster wird jedoch nicht unterstützt die **"Auto"** Fenster.

Betrachten Sie als Nächstes die **"lokal"** Fenster. Die **"lokal"** Fenster zeigt die Variablen, die derzeit im Gültigkeitsbereich befinden.

![Fenster "lokal"](../debugger/media/dbg-tour-locals-window.png "Fenster "lokal"")

In diesem Beispiel wird die `this` und das Objekt `f` befinden sich im Gültigkeitsbereich. Weitere Informationen finden Sie unter [Untersuchen von Variablen im Fenster "lokal" und "Auto"](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Festlegen einer Überwachung

Können Sie eine **Überwachen** Fenster auf angeben, eine Variable (oder ein Ausdruck), die Sie Auge behalten möchten.

Während des Debuggens, mit der rechten Maustaste in ein Objekt, und wählen Sie **Überwachung hinzufügen**.

![Überwachung (Fenster)](../debugger/media/dbg-tour-watch-window.png "Fenster "überwachen"")

In diesem Beispiel haben Sie eine Überwachung, legen Sie für die `File` -Objekt, und Sie sehen den Wert ändern, wie Sie mithilfe des Debuggers verschieben. Im Gegensatz zu den anderen Variablenfenstern die **Überwachen** Windows den Variablen immer anzeigen, dass Sie beobachten sind (sie sind abgeblendet, wenn außerhalb des gültigen Bereichs).

Weitere Informationen finden Sie unter [legen Sie eine Überwachung mit der überwachen "und" Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Die Aufrufliste überprüfen

Klicken Sie auf die **Aufrufliste** Fenster während des Debuggens, das standardmäßig in der unteren rechten Bereich geöffnet ist.

![Überprüfen Sie die Aufrufliste](../debugger/media/dbg-tour-call-stack.png "die Aufrufliste überprüfen")

Die **Aufrufliste** Fenster zeigt die Reihenfolge, in der Funktionen und Methoden werden aufgerufen. Die oberste Zeile zeigt die aktuelle Funktion (die `Update` Methode in diesem Beispiel). Die zweite Zeile zeigt, dass `Update` aufgerufen wurde, aus der `Path.set` -Eigenschaft, und So weiter. Die Aufrufliste ist eine gute Möglichkeit, untersuchen und Verstehen der Ausführungsfluss einer app.

> [!NOTE]
> Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse.

Doppelklicken Sie auf eine Codezeile wechseln betrachten, Quellcode und ändert, die auch den aktuellen Bereich, der vom Debugger geprüft wird. Den Debugger wird dies nicht weitergeführt.

Sie können auch Kontextmenüs aus der **Aufrufliste** Fenster aus, um andere Aufgaben ausführen. Sie können z. B. Haltepunkte in bestimmten Funktionen einzufügen, neu starten, die app mithilfe **Ausführen bis Cursor**, und fahren Sie Quellcode überprüfen. Finden Sie unter [Vorgehensweise: untersuchen die Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a>Eine Ausnahme zu untersuchen

Wenn Ihre app eine Ausnahme auslöst, wechselt der Debugger an die Codezeile, die die Ausnahme ausgelöst hat.
     
![Ausnahmen-Hilfe](../debugger/media/dbg-tour-exception-helper.png "Ausnahmen-Hilfe")

In diesem Beispiel wird die **Ausnahmen-Hilfe** erfahren Sie, eine `System.Argument` Ausnahme und eine Fehlermeldung, die besagt, dass der Pfad nicht um ein ungültiges Format ist. Daher wissen, dass der Fehler aufgetreten ist, auf eine Methode oder Funktion-Argument.

In diesem Beispiel wird die `DirectoryInfo` Aufruf der angegebene Fehler trat auf die leere Zeichenfolge, die in der `value` Variable.

Ausnahmen-Hilfe ist eine großartige Funktion, die Sie beim Debuggen von Fehlern helfen. Sie können auch Aktionen wie die Ansicht Fehlerdetails und Hinzufügen einer Überwachung von Ausnahmen-Hilfe. Oder, bei Bedarf können Sie Bedingungen für die bestimmte Ausnahme ändern.

>  [!NOTE] 
> Ausnahmen-Hilfe ersetzt der Ausnahmen-Assistent in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Erweitern Sie die **Ausnahmeeinstellungen** Knoten, um weitere Optionen zum Behandeln dieser Ausnahmetyp, aber Sie müssen nicht ändert nichts für diesen Überblick!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debuggen von Livedaten ASP.NET-apps in Azure App Service

die **Momentaufnahme Debugger** eine Momentaufnahme Ihrer Anwendungen in Produktion aufgenommen, wenn Code, der Sie interessiert sind, ausgeführt. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

![Starten des Debuggers Momentaufnahme](../debugger/media/snapshot-launch.png "Starten des Debuggers Momentaufnahme")

Momentaufnahme-Auflistung ist verfügbar für ASP.NET-Anwendungen in Azure App Service ausgeführt. ASP.NET-Anwendungen müssen ausgeführt werden, auf .NET Framework 4.6.1 oder höher, und ASP.NET Core-Anwendungen müssen auf .NET Core 2.0 oder höher auf Windows ausgeführt werden.

Weitere Informationen finden Sie unter [live ASP.NET-apps, die mit der Snapshot-Debugger Debuggen](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Anzeigen von Momentaufnahmen mit IntelliTrace Schritt hinten (Visual Studio Enterprise)

**IntelliTrace Schritt hinten** automatisch Schritt Ereignis wird eine Momentaufnahme der Anwendung auf jedem haltepunktereignissen und den Debugger. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

![Schrittweise rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png  "Schritt rückwärts und Vorwärts-Schaltflächen")  

Weitere Informationen finden Sie auf der Seite [View snapshots using IntelliTrace step-back (Anzeigen von Momentaufnahmen mithilfe des IntelliTrace-Features „Step-back“)](../debugger/how-to-use-intellitrace-step-back.md).

## <a name="more-features-to-look-at"></a>Weitere Features ansehen

-   [Debugger, Tipps und Tricks](../debugger/debugger-tips-and-tricks.md) erfahren Sie, wie Ihre Produktivität mit dem Debugger.

-   [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md) für eine Teilmenge von Sprachen (C#-, C++, Visual Basic), die Funktion bearbeiten und fortfahren können Sie Code in der Mitte einer Debugsitzung zu bearbeiten.

-   [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md) beschreibt das Debuggen von Multithreadanwendungen verwendet werden können. 

-   [Remotedebuggen](../debugger/remote-debugging.md) beschreibt das Debuggen von apps, die auf anderen Computern oder Geräten ausgeführt werden. 
  
-   [IntelliTrace](../debugger/intellitrace.md) beschreibt die Funktion "IntelliTrace" in Visual Studio Enterprise. Sie können es Datensatz und Trace Ausführungsverlauf des Codes verwenden.

-   [Netzwerkauslastung](../profiling/network-usage.md) beschreibt ein Profilerstellungstool, die Sie zum Debuggen von Webdiensten und anderen Netzwerkressourcen in universellen Windows-Apps (UWP) verwenden können. Verwenden Sie das Tool, um Nutzlasten zu untersuchen.

-   [Debug Interface Access SDK](../debugger/debug-interface-access/debug-interface-access-sdk.md) beschreibt das Microsoft Debug Interface Access Software Development Kit (DIA SDK). Das DIA SDK bietet Zugriff auf Debuginformationen, die in von Microsoft-Postcompilertools generierten Programmdatenbankdateien (PDB-Format) gespeichert werden.  

## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)
