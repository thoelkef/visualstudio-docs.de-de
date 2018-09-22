---
title: Erste Schritte zum Debuggen in Visual Studio 2017
description: Erste Schritte zum Debuggen von Anwendungen mit Visual Studio-debugger
ms.custom: mvc
ms.date: 06/15/2018
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
ms.openlocfilehash: e2339dcfe80e994b8bc9062d137263d3b25d274d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542415"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Ein erster Blick auf die Visual Studio-Debugger

Dieses Thema führt die Debugger-Tools von Visual Studio bereitgestellt. Im Visual Studio-Kontext bei der Sie *Debuggen Ihrer app*, es in der Regel bedeutet, dass Sie die Anwendung mit dem angefügten Debugger ausgeführt werden (d. h. im Debuggermodus). Wenn Sie dies tun, wird der Debugger bietet viele Möglichkeiten, um festzustellen, was den Status Ihres Codes während der Ausführung. Sie können den Code schrittweise durchlaufen und die Werte in Variablen gespeicherten, Sie können Überwachungen Variablen angezeigt, wenn die Werte ändern, können Sie den Ausführungspfad des Codes untersuchen Et al. Wenn dies das erste Mal, die Sie versucht haben ist, um Code zu debuggen, sollten Sie lesen [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md) vor dem Durcharbeiten dieses Themas.

Die hier beschriebenen Features gelten für c#, C++, Visual Basic, JavaScript und anderen (außer den) von Visual Studio unterstützten Sprachen zur Verfügung.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

Um zu debuggen, müssen Sie Ihre app mit dem an den app-Prozess angefügten Debugger zu starten. **F5** (**Debuggen > Debuggen starten**) ist die gängigste Methode dafür. Jedoch jetzt Sie keine Haltepunkte, überprüfen Sie Ihre app festgelegt haben, können code, sodass wir zuerst und dann das debugging starten. Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. 

Wenn Sie eine Datei im Code-Editor geöffnet haben, können Sie einen Haltepunkt festlegen, indem Sie auf den Rand links neben einer Codezeile.

![Festlegen eines Haltepunkts](../debugger/media/dbg-tour-set-a-breakpoint.gif "Festlegen eines Haltepunkts")

Drücken Sie **F5** (**Debuggen > Debuggen starten**) oder die **Debuggen starten** Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten ") in der Symbolleiste Debuggen und der Debugger ausgeführt wird, bis zum ersten Breakpoint, der es auftritt. Wenn die app noch nicht ausgeführt wird, wird von F5 wird der Debugger gestartet und wird am ersten Haltepunkt angehalten.

Haltepunkte sind eine nützliche Funktion, wenn Sie wissen, die Zeile des Codes oder des Codeabschnitts, die Sie genauer untersuchen möchten.

## <a name="navigate"></a> Navigieren Sie im Code im Debugger verwenden diese Befehle

Geben wir die Tastenkombinationen für die meisten Befehle, da sie Navigation durch Ihren app-Code beschleunigen. (Die entsprechende Befehle z. B. Menübefehle in Klammern angezeigt werden.)

Um Ihre app mit dem angefügten Debugger zu starten, drücken Sie die **F11** (**Debuggen > Einzelschritt**). F11 wird die **Einzelschritt** -Befehl aus, und setzt die app Ausführung einer Anweisung zu einem Zeitpunkt. Wenn Sie die app durch Drücken von F11 starten, unterbricht der Debugger, bei der ersten Anweisung, die ausgeführt wird.

![F11 Einzelschritt](../debugger/media/dbg-tour-f11.png "F11 Einzelschritt")

Der gelbe Pfeil stellt die Anweisung auf der der Debugger angehalten ist, die auch app-Ausführung an der gleichen Stelle unterbricht (diese Anweisung wurde noch nicht ausgeführt).

F11 ist eine gute Möglichkeit, den Ausführungsablauf in die meisten Details zu überprüfen. (Um im Code schneller zu verschieben, zeigen wir Ihnen einige weitere Optionen.) Standardmäßig überspringt der Debugger nicht benutzerseitiger Code (Sie weitere Informationen finden Sie unter [nur mein Code](../debugger/just-my-code.md)).

>[!NOTE]
> In verwaltetem Code sehen Sie ein Dialogfeld gefragt, wenn Sie benachrichtigt werden, wenn Sie automatisch Eigenschaften und Operatoren überspringen (Standardverhalten) ausführen möchten. Wenn Sie die Einstellung ändern möchten später deaktivieren **Eigenschaften und Operatoren überspringen** festlegen in der **Tools > Optionen** Menü unter **Debuggen**.

## <a name="step-over-code-to-skip-functions"></a>Prozedurschritt für Code, um Funktionen zu überspringen.

Wenn Sie eine einzige Zeile Code, die eine Funktion oder ein Methodenaufruf ist verwenden, drücken Sie **F10** (**Debuggen > Prozedurschritt**) anstelle von F11.

F10 wechselt den Debugger ohne einen Einzelschritt in die Funktionen oder Methoden in Ihrem app-Code (der Code wird immer noch ausgeführt). Durch Drücken von F10, können Sie über Code überspringen, denen Sie nicht interessiert sind. Auf diese Weise können Sie schnell Code abrufen, denen Sie interessant sind.

## <a name="step-into-a-property"></a>Einzelschritt in eine Eigenschaft

Erwähnt, wird standardmäßig der Debugger überspringt aus verwalteten Eigenschaften und Felder, aber die **Einzelschritt in Angabe** Befehl können Sie dieses Verhalten außer Kraft zu setzen.

Mit der rechten Maustaste auf eine Eigenschaft oder ein Feld, und wählen Sie **Einzelschritt in Angabe**, wählen Sie dann eine der verfügbaren Optionen.

![Einzelschritt in die spezifische](../debugger/media/dbg-tour-step-into-specific.png "Einzelschritt in Angabe")

In diesem Beispiel **Einzelschritt in Angabe** bringt uns auf den Code für `Path.set`.

![Einzelschritt in die spezifische](../debugger/media/dbg-tour-step-into-specific-2.png "Einzelschritt in Angabe")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Führen Sie auf einen Zeitpunkt in Ihrem Code schnell mit der Maus

Zeigen Sie im Debugger, die eine einzige Zeile Code, bis die **Ausführung bis Klick** (Ausführung bis hier ausführen) Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") auf der linken Seite angezeigt wird.

![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click-2.png "Ausführung bis Klick")

> [!NOTE]
> Die **Ausführung bis Klick** (Ausführung bis hier ausführen) Schaltfläche ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Klicken Sie auf die **Ausführung bis Klick** Schaltfläche "(Ausführung bis hier ausführen)". Der Debugger setzt auf die Zeile des Codes, auf Sie geklickt hat.

Mit dieser Schaltfläche ähnelt der als temporären Haltepunkt festlegen. Dieser Befehl ist auch nützlich für die Umgehung sich schnell innerhalb eines sichtbaren Bereichs des app-Codes. Sie können **Ausführung bis Klick** in einer geöffneten Datei.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Fahren Sie fort, den Debugger aus der aktuellen Funktion

In einigen Fällen möchten Sie die Debugsitzung weiterhin, sondern fahren Sie fort, den Debugger über die aktuelle Funktion bis hin.

Drücken Sie **UMSCHALT + F11** (oder **Debuggen > Ausführen bis Rücksprung**).

Mit diesem Befehl wird die app-Ausführung fortgesetzt (und den Debugger wechselt), bis die aktuelle Funktion zurückkehrt.

## <a name="run-to-cursor"></a>Ausführen bis Cursor

Beenden Sie den Debugger durch Drücken der **Debuggen beenden** rote Schaltfläche ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") oder **UMSCHALT**  +  **F5**.

Klicken Sie auf eine Zeile des Codes in Ihrer app, und wählen Sie **Ausführen bis Cursor**. Dieser Befehl startet das debugging und legt einen temporären Haltepunkt für die aktuelle Zeile des Codes.

![Ausführen bis Cursor](../debugger/media/dbg-tour-run-to-cursor.png "Ausführen bis Cursor")

Wenn Sie Haltepunkte festgelegt haben, hält sich der Debugger am ersten Haltepunkt, den er erreicht.

Drücken Sie **F5** aus, bis Sie die Zeile des Codes ausgewählt, in dem Sie **Ausführen bis Cursor**.

Dieser Befehl ist nützlich, wenn Sie Code bearbeiten und schnell einen temporären Haltepunkt festlegen und starten Sie den Debugger zur gleichen Zeit möchten.

> [!NOTE]
> Sie können **Ausführen bis Cursor** in die **Aufrufliste** Fenster während des Debuggens.

## <a name="restart-your-app-quickly"></a>Starten Sie Ihre app schnell neu.

Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "App neu starten") der Debug-Symbolleiste (**STRG + UMSCHALT + F5**).

Beim Drücken **Neustart**, denn Sie spart Zeit und beenden die app und erneutes Starten des Debuggers. Der Debugger hält am ersten Haltepunkt, der erreicht wird, indem Sie Code ausführen.

Wenn Sie den Debugger beenden und in den Codeeditor zu erhalten möchten, können Sie das rote Beenden drücken ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") Schaltfläche anstelle von **Neustart**.

## <a name="inspect-variables-with-data-tips"></a>Untersuchen Sie Variablen mit den Datentipps

Nun, dass Sie Ihr ein wenig vertraut sind, müssen Sie eine gute Gelegenheit, starten Sie den app-Status (Variablen) mit dem Debugger überprüfen. Funktionen, die Ihnen ermöglichen, Variablen untersuchen sind einige der nützlichsten Funktionen des Debuggers, und es gibt verschiedene Möglichkeiten dafür. Häufig, wenn Sie versuchen, ein Problem debuggen können, sind Sie versucht, finden Sie heraus, ob Variablen die Werte speichern, die voraussichtlich in einem bestimmten app-Zustand über.

Während im Debugger angehalten wird, zeigen Sie ein Objekt mit der Maus, und Sie sehen, dass der Standardwert der Eigenschaft (in diesem Beispiel ist der Dateiname `market 031.jpg` ist der Standardwert der Eigenschaft).

![Anzeigen eines Datentipps](../debugger/media/dbg-tour-data-tips.gif "einen Datentipp anzeigen")

Erweitern Sie das Objekt, um alle ihre Eigenschaften anzuzeigen (z. B. die `FullPath` in diesem Beispiel).

Häufig, wenn Debuggen, sollten Sie eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte, und der Datentipps sind eine gute Möglichkeit dafür.

> [!TIP]
> Die meisten unterstützten Sprachen können Sie Code in der Mitte einer Debugsitzung bearbeiten. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen Sie Variablen mit den Fenstern "Auto" und "lokal"

Betrachten Sie während des Debuggens die **"Auto"** Fenster am unteren Rand der Code-Editor.

![Fenster Auto Fenster](../debugger/media/dbg-tour-autos-window.png "Fenster \"Auto\"")

In der **"Auto"** angezeigt Variablen zusammen mit ihren aktuellen Wert und deren Typ. Die **"Auto"** Fenster zeigt alle Variablen, die in der aktuellen Zeile oder die vorangehende Zeile verwendet wird (In C++ wird das Fenster zeigt Variablen in den vorherigen drei Zeilen des Codes. Dokumentation für die sprachspezifisches Verhalten).

> [!NOTE]
> In JavaScript die **"lokal"** Fenster wird nicht unterstützt die **"Auto"** Fenster.

Betrachten Sie als Nächstes die **"lokal"** Fenster. Die **"lokal"** Fenster zeigt die Variablen, die derzeit im Gültigkeitsbereich befinden.

![Fenster "lokal"](../debugger/media/dbg-tour-locals-window.png "Fenster \"lokal\"")

In diesem Beispiel die `this` Objekt und das Objekt `f` befinden sich im Gültigkeitsbereich. Weitere Informationen finden Sie unter [Überprüfen von Variablen in der "Auto" und "lokal" Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Set a Watch festlegen

Können Sie eine **Watch** Fenster, geben auf eine Variable (oder eines Ausdrucks), die Sie im Auge zu behalten möchten.

Während des Debuggens mit der rechten Maustaste ein Objekt, und wählen Sie **Überwachung hinzufügen**.

![Überwachung (Fenster)](../debugger/media/dbg-tour-watch-window.png "Fenster \"überwachen\"")

In diesem Beispiel haben Sie eine Überwachung, legen Sie für die `f` -Objekt, und Sie sehen den Wert ändern, wie Sie den Debugger verschieben. Im Gegensatz zu anderen Variablenfenstern die **Watch** Windows den Variablen immer anzeigen, dass Sie überwachen (sie sind ausgegraut, wenn außerhalb des gültigen Bereichs).

Weitere Informationen finden Sie unter [festlegen eine Überwachung mit dem überwachen und Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Die Aufrufliste überprüfen

Klicken Sie auf die **Aufrufliste** Fenster während des Debuggens, die standardmäßig in der unteren rechten Bereich geöffnet ist.

![Überprüfen Sie die Aufrufliste](../debugger/media/dbg-tour-call-stack.png "die Aufrufliste überprüfen")

Die **Aufrufliste** Fenster zeigt die Reihenfolge, in dem Methoden und Funktionen werden aufgerufen. Der obersten Zeile wird die aktuelle Funktion (der `Update` -Methode in diesem Beispiel). Die zweite Zeile zeigt, dass `Update` aufgerufen wurde, aus der `Path.set` -Eigenschaft, und So weiter. Die Aufrufliste ist eine gute Möglichkeit zum Untersuchen und verstehen, den Ausführungsablauf der app.

> [!NOTE]
> Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse.

Doppelklicken Sie auf eine einzige Zeile Code zu diesem Quellcode betrachten und ändert, die ebenfalls den aktuellen Bereich, der vom Debugger überprüft werden. Dies ist den Debugger nicht weitergeführt.

Sie können auch die Kontextmenüs von der **Aufrufliste** Fenster aus, um andere Dinge tun. Sie können z. B. Haltepunkte in bestimmten Funktionen einzufügen, Ihrer app über einen Neustart **Ausführen bis Cursor**, und wechseln Quellcode untersuchen. Finden Sie unter [Vorgehensweise: untersuchen die Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Untersuchen einer Ausnahme

Wenn Ihre app eine Ausnahme auslöst, ruft der Debugger die Codezeile, die die Ausnahme ausgelöst hat.

![Ausnahmen-Hilfe](../debugger/media/dbg-tour-exception-helper.png "Ausnahmen-Hilfe")

In diesem Beispiel die **Ausnahmehilfsprogramm** erfahren Sie, eine `System.Argument` Ausnahme und eine Fehlermeldung, die besagt, dass der Pfad kein ungültiges Format. Wir wissen also, dass der Fehler aufgetreten ist, auf eine Methode oder Funktion-Argument.

In diesem Beispiel die `DirectoryInfo` Aufruf hat den Fehler, auf die leere Zeichenfolge, die in der `value` Variable.

Die Ausnahmen-Hilfe ist eine großartige Funktion, die Sie das Debuggen von Fehlern unterstützen. Sie können auch Dinge wie Ansicht Fehlerdetails und Hinzufügen einer Überwachung aus der Ausnahme-Hilfe. Oder, bei Bedarf können Sie Bedingungen für eine bestimmte Ausnahme ändern.

>  [!NOTE]
> Die Ausnahmen-Hilfe, ersetzt der Ausnahmen-Assistent in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Erweitern Sie die **Ausnahmeeinstellungen** Knoten finden weitere Möglichkeiten zum Behandeln dieser Ausnahmetyp, aber Sie müssen nicht alles für diesen Überblick zu ändern.

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debug live ASP.NET-Apps in Azure App Service

die **Momentaufnahmedebugger** eine Momentaufnahme Ihrer Apps in der Produktion bei der Ausführung von Code, der Sie interessiert sind. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

![Starten Sie den momentaufnahmedebugger](../debugger/media/snapshot-launch.png "der Snapshot-Debugger")

Erfassung von Momentaufnahmen ist verfügbar für ASP.NET-Anwendungen in Azure App Service ausgeführt. ASP.NET-Anwendungen müssen ausgeführt werden, auf .NET Framework 4.6.1 oder höher, und ASP.NET Core-Anwendungen müssen auf .NET Core 2.0 oder höher unter Windows ausgeführt werden.

Weitere Informationen finden Sie unter [Debug live ASP.NET-Apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Anzeigen von Momentaufnahmen mit IntelliTrace Rückschritt (Visual Studio Enterprise)

**IntelliTrace Rückschritt** automatisch eine Momentaufnahme Ihrer Anwendung in jedem Breakpoint und Debuggerschritt Schrittereignis. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

![Schrittweise rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png  "Schritt rückwärts und Vorwärts-Schaltflächen")

Weitere Informationen finden Sie unter den [überprüfen Sie die vorherigen app-Status, die mithilfe von IntelliTrace](../debugger/view-historical-application-state.md) Seite.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie einen kurzen Blick auf zahlreiche Debuggerfunktionen mussten. Sie sollten eine eingehendere Betrachtung diese Funktionen mit einer beispielanwendung

> [!div class="nextstepaction"]
> [Lernen Sie das Debuggen mit Visual Studio](../debugger/getting-started-with-the-debugger.md)
