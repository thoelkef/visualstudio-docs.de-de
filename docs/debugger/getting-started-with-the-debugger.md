---
title: Weitere Informationen zum Debuggen mit Visual Studio | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords: debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a09e0c54f1d7f0e49f08ddf65afbeb030a7087f1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>Weitere Informationen Sie zum Debuggen mit Visual Studio

Dieses Thema enthält die Funktionen von Visual Studio-Debugger in eine schrittweise exemplarische Vorgehensweise. Wenn Sie einen Überblick über die Funktionen des Debuggers auf höherer Ebene möchten, finden Sie unter [Debugger Feature Tour](../debugger/debugger-feature-tour.md).

Sie können entweder entlang gelesen, um die Funktionen des Debuggers finden Sie unter, oder Sie können das vollständige Beispiel verwendet die Funktion Tour herunterladen und führen Sie die Schritte selbst. Wechseln Sie zu, um das Beispiel herunterzuladen und nachvollziehen, [Photo Viewer Demo](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [In diesem Video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) Debuggen, die ähnliche Schritte anzeigt. |

Obwohl die Demo-app c# ist, gelten die Funktionen für C++, Visual Basic, JavaScript und anderen Sprachen (falls nicht anders) von Visual Studio unterstützt.

## <a name="start-the-debugger"></a>Starten Sie den Debugger an!

1. Um diese Schritte in Visual Studio folgen, laden Sie das Beispiel [auf dieser Seite](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Sie müssen Visual Studio mit .NET Desktop Entwicklungsaufwand zum Ausführen der app, die wir verwenden, in der Demo installieren.

2. Entpacken Sie das Projekt.

3. Öffnen Sie Visual Studio, und wählen Sie die **Datei > Öffnen** Menü Befehl aus, und wählen Sie dann **Projekt/Projektmappe**, und öffnen Sie den Ordner, in dem Sie das Projekt heruntergeladen haben.

     ![Öffnen Sie das Beispielprojekt](../debugger/media/dbg-tour-open-project.png "Projekt öffnen")

3. Öffnen Sie die WPF-Foto-Viewer-Demo > C#-Ordner, wählen Sie die Datei photoapp.sln und **öffnen**.

     Das Projekt in Visual Studio wird geöffnet. Projektmappen-Explorer im rechten Bereich zeigt Sie die Projektdateien.

    ![Projektmappen-Explorer-Dateien](../debugger/media/dbg-tour-solution-explorer.png "Projektmappen-Explorer")

4. Drücken Sie F5 (**Debuggen > Debuggen starten** oder **Debuggen starten** Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debuggen") in der Debug-Symbolleiste).

     ![Foto-Viewer-Apps](../debugger/media/dbg-tour-wpf-app.png "Foto-Viewer-App")

     F5 wird die Anwendung gestartet, mit dem Debugger, die auf den app-Prozess, sondern rechts angefügt werden, nachdem wir noch keine Haltepunkte hinzugefügt oder "Fertig" nichts Besonderes, um den Code zu untersuchen. Daher die app gerade geladen wird, und Sie sehen, dass die Bilder.

     In dieser Tour wir diese app über den Debugger näher betrachten und erhalten einen Blick auf der Debugger-Funktionen.

5. Beenden Sie den Debugger durch Drücken zum Beenden der rote ![Beenden des Debuggens](../debugger/media/dbg-tour-stop-debugging.png "Beenden des Debuggens") Schaltfläche.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

Zum Debuggen, müssen Sie Ihre app mit dem an den app-Prozess angefügten Debugger zu starten.

1. In der `MainWindow` Konstruktor von "MainWindow.Xaml.cs", einen Haltepunkt festlegen, indem Sie auf den linken Rand der ersten Zeile des Codes.

     ![Festlegen eines Haltepunkts](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Drücken Sie F5, oder die **Debuggen** Schaltfläche, die app gestartet wird, und der Debugger führt die Codezeile, in dem Sie den Haltepunkt festgelegt haben.

    Der gelbe Pfeil stellt die Anweisung auf der der Debugger angehalten, die auch app-Ausführung an der gleichen Stelle unterbricht (diese Anweisung wurde noch nicht ausgeführt).

    F5 wird das Ausführen der app zum nächsten Haltepunkt fortgesetzt. (Wenn die app noch nicht ausgeführt wird, F5 wird der Debugger gestartet und am ersten Haltepunkt beendet wird.)

    Haltepunkte sind nützlich, wenn Sie wissen, die Zeile des Codes oder Abschnitt des Codes, die Sie im Detail untersuchen möchten.

## <a name="restart-your-app-quickly"></a>Die app schnell neu startet

1. Klicken Sie auf die **Neustart** ![App starten](../debugger/media/dbg-tour-restart.png "RestartApp") auf der Debug-Symbolleiste (STRG + UMSCHALT + F5).

    Wenn Sie drücken **Neustart**, es sparen Sie Zeit und Beenden der app und der Debugger neu gestartet. Der Debugger hält am ersten Haltepunkt, der erreicht wird, indem Sie Code ausführen.

    Der Debugger hält wieder am Haltepunkt, in Festlegen der `MainWindow` Konstruktor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren Sie im Code im Debugger mit Schritt-Befehlen

Meistens wir Tastenkombinationen verwenden, die hier ist eine gute Möglichkeit, erhalten beim Ausführen der app im Debugger (entsprechende Befehle wie z. B. im Menü Befehle sind in Klammern angezeigt).

1. Drücken Sie F11 (**Debuggen > Einzelschritt**) zweimal, um die Ausführung der app zu wechseln der `InitializeComponent()` Funktion.

     ![Verwenden Sie F11, um Einzelschritt Code](../debugger/media/dbg-tour-f11.png "F11 Einzelschritt")

     F11 ist die **Einzelschritt** Befehl und setzt die app Ausführung einer Anweisung zu einem Zeitpunkt. F11 ist eine gute Möglichkeit, die den Ausführungsfluss in den meisten Details zu überprüfen. (Um den Code schneller zu durchlaufen, erfahren Sie einige andere Optionen auch.) Standardmäßig überspringt der Debugger Nichtbenutzercode (Wenn Sie mehr Details anzeigen möchten, finden Sie unter [nur mein Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > In verwaltetem Code sehen Sie ein Dialogfeld gefragt, ob Sie benachrichtigt werden, wenn Sie automatisch Eigenschaften und Operatoren (Standardverhalten) überspringen möchten. Wenn Sie die Einstellung ändern möchten höher deaktivieren **Eigenschaften und Operatoren überspringen** festlegen in der **Tools > Optionen** Menü unter **Debuggen**.

2. Drücken Sie F10 (**Debuggen > Prozedurschritt**) mehrmals bis auf die erste Zeile des Codes in der Debugger hält die `OnApplicationStartup` -Ereignishandler.

     ![Verwenden Sie F10, um Prozedurschritt Code](../debugger/media/dbg-tour-f10-step-over.png "F10 Prozedurschritt")

     F10 setzt des Debuggers, ohne die schrittweise Ausführung von Funktionen oder Methoden in Ihrem app-Code (der Code wird noch ausgeführt). Durch Drücken der Taste F10 auf die `InitializeComponent` Methodenaufruf (statt F11), die wir über den Implementierungscode für übersprungen `InitializeComponent` (welche Maybe wir nicht interessant jetzt sind sind).

## <a name="step-into-a-property"></a>Einzelschritt in eine Eigenschaft

1. Mit der Debugger, die auf diese Codezeile angehalten werden:

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Mit der rechten Maustaste auf die Zeile des Codes, und wählen Sie **Schritt in bestimmten**, klicken Sie dann **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Verwenden Sie bestimmte Funktion "Einzelschritt"](../debugger/media/dbg-tour-step-into-specific.png "in bestimmten Schritt")

    Erwähnt, wird standardmäßig der Debugger überspringt aus verwalteten Eigenschaften und Felder, aber die **Schritt in bestimmten** Befehl können Sie dieses Verhalten außer Kraft setzen. Jetzt möchten wir sehen, was geschieht, wenn die `Path.set` Eigenschaft-Setter ausgeführt wird. **In bestimmten Schritt** uns, ruft der `Path.set` im folgenden code.

     ![Ergebnis der Schritte in bestimmten](../debugger/media/dbg-tour-step-into-specific-2.png "in bestimmten Schritt")

     Die `Update` Methode in diesem Code scheint es interessant, sein könnte dies der Fall ist, können mit dem Debugger können Sie diesen Code nah untersuchen.

5. Zeigen Sie auf die `Update` Methode erst über die grüne **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick") auf der linken Seite angezeigt wird.

     ![Verwenden Sie ausführen, klicken Sie auf Funktion](../debugger/media/dbg-tour-run-to-click-2.png "ausführen, klicken Sie auf")

    >  [!NOTE] 
    > Die **ausführen, klicken Sie auf** Schaltfläche ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Wenn die grünen Pfeilschaltfläche nicht angezeigt wird, verwenden Sie F11 in diesem Beispiel wird stattdessen an den Debugger zu gelangen.

6. Klicken Sie auf die **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mit dieser Schaltfläche ähnelt der einen temporären Haltepunkt festlegen. **Klicken Sie auf Ausführen** ist praktisch, schnell Umgehung innerhalb eines sichtbaren Bereichs des app-Code (Sie können in einer geöffneten Datei klicken).

    Der Debugger setzt auf den `Update` methodenimplementierung.

7. Drücken Sie F11, um einen Einzelschritt in die `Update` Methode.

     ![Einzelschritt in die Updatemethode Ergebnis](../debugger/media/dbg-tour-update-method.png "Schritt in Update-Methode")

    Hier finden wir weitere Code, der die interessanten; die app nur noch alle *.jpg-Dateien in einem bestimmten Verzeichnis befinden, und erstellen dann ein Foto-Objekt für jede Datei. Dieser Code erhalten Sie eine gute Gelegenheit handelt, überprüfen den app-Zustand (Variablen) mit dem Debugger starten. Wir werden, die in den nächsten Abschnitten dieses Lernprogramm durchführen.

    Funktionen, die Ihnen ermöglichen, überprüfen Sie die Variablen sind eine der nützlichsten Funktionen des Debuggers, und es gibt verschiedene Möglichkeiten zu diesem Zweck. Häufig, wenn Sie versuchen, ein Problem debuggen können, versuchen Sie, herauszufinden, ob Variablen die Werte, die sie zu einem bestimmten Zeitpunkt verfügen voraussichtlich gespeichert sind.

## <a name="examine-the-call-stack"></a>Die Aufrufliste überprüfen

- Bei angehaltener in der `Update` -Methode, klicken Sie auf die **Aufrufliste** Fenster, das standardmäßig in der unteren rechten Bereich geöffnet ist.

     ![Die Aufrufliste überprüfen](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

    Die **Aufrufliste** Fenster zeigt die Reihenfolge, in der Funktionen und Methoden werden aufgerufen. Die oberste Zeile zeigt die aktuelle Funktion (die `Update` Methode in der app Tour). Die zweite Zeile zeigt, dass `Update` aufgerufen wurde, aus der `Path.set` -Eigenschaft, und So weiter.

    >  [!NOTE]
    > Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse.

    Die Aufrufliste ist eine gute Möglichkeit, untersuchen und Verstehen der Ausführungsfluss einer app.

    Doppelklicken Sie auf eine Codezeile wechseln betrachten, Quellcode und ändert, die auch den aktuellen Bereich, der vom Debugger geprüft wird. Den Debugger weitergeführt diese Aktion nicht.

    Sie können auch Kontextmenüs aus der **Aufrufliste** Fenster aus, um andere Aufgaben ausführen. Sie können z. B. Legen Sie Haltepunkte in der angegebenen Funktionen, kann den Debugger mit **Ausführen bis Cursor**, und wechseln Sie Quellcode zu untersuchen. Weitere Informationen finden Sie unter [Vorgehensweise: Untersuchen der Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Ausführen bis Rücksprung

Angenommen, Sie haben überprüft die `Update` Methode in Data.cs, und Sie möchten, aus der Funktion erhalten bleibt jedoch im Debugger. Hierzu können Sie mithilfe der **Ausführen bis Rücksprung** Befehl.

1. Drücken Sie UMSCHALT + F11 (oder **Debuggen > Ausführen bis Rücksprung**).

     Dieser Befehl setzt die app-Ausführung (und den Debugger setzt) bis die aktuelle Funktion zurückgibt.

     Sie muss in der `Update` Methodenaufruf in Data.cs.

2. Drücken Sie UMSCHALT + F11 erneut und der Debugger wechselt der Aufrufliste zurück an den `OnApplicationStartup` -Ereignishandler.

## <a name="run-to-cursor"></a>Ausführen bis Cursor

1. Wählen Sie die **Beenden des Debuggens** rote Schaltfläche ![Beenden des Debuggens](../debugger/media/dbg-tour-stop-debugging.png "Beenden des Debuggens") oder UMSCHALT + F5.

2. In der `Update` Methode in Data.cs, Maustaste die `Add` -Methodenaufruf, und wählen Sie **Ausführen bis Cursor**. Dieser Befehl startet das Debuggen und legt einen temporären Haltepunkt in der aktuellen Zeile des Codes.

     ![Verwenden Sie das Ausführen bis Cursor Feature](../debugger/media/dbg-tour-run-to-cursor.png "Ausführen bis Cursor")

    Sie sollten angehalten werden, an dem Haltepunkt in `MainWindow` (da dies der erste Haltepunkt ist festgelegt werden).

3. Drücken Sie F5, um zum Wechseln der `Add` Methode, die Sie ausgewählt haben, in denen **Ausführen bis Cursor**.

    Dieser Befehl ist nützlich, wenn Sie Code bearbeiten und schnell einen temporären Haltepunkt festlegen und den Debugger starten möchten.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsflusses

1. Mit dem Debugger angehalten werden soll, auf die `Add` -Methodenaufruf, verwenden Sie die Maus auf den gelben Pfeil (der Ausführungszeiger) auf der linken Seite und den gelben Pfeil, um eine Zeile nach oben verschieben der `foreach` Schleife.

     ![Verschieben der Ausführungszeiger](../debugger/media/dbg-tour-move-the-execution-pointer.gif "der Ausführungszeiger verschieben")

    Durch eine Änderung der Ausführungsfluss, können Sie Aktionen wie Ausführungspfade für anderen Code zu testen, oder führen Sie Code erneut aus, ohne den Debugger neu gestartet.

2. Jetzt, drücken Sie F5.

    Sie sehen, dass die Bilder, die im Fenster der Anwendung hinzugefügt. Da Sie im Code erneut ausführen, werden die `foreach` Schleife, einige Images wurden zweimal hinzugefügt!
    
    > [!WARNING]
    > Häufig müssen Sie mit dieser Funktion vorsichtig sein, und Sie eine Warnung in der QuickInfo angezeigt. Andere Warnungen, möglicherweise zu angezeigt werden. Verschieben den Zeiger kann nicht die Anwendung in einem früheren app-Status wiederhergestellt.

## <a name="inspect-variables-with-data-tips"></a>Überprüfung von Variablen mit Datentipps

1. Data.cs in die Foto-Viewer-Demo-app Öffnen der rechten Maustaste auf die `private void Update` Funktionsdeklaration, und wählen Sie **Ausführen bis Cursor** (beendet die app zuerst, wenn er bereits ausgeführt wird).

    Dadurch wird die app mit dem angefügten Debugger angehalten. Dadurch können wir den Status zu überprüfen.

2. Zeigen Sie auf die `Add` -Methodenaufruf, und klicken Sie auf die **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Jetzt, zeigen Sie auf das Objekt "Datei" (`f`), und Sie sehen, dass der Standardwert der Eigenschaft, die Dateinamen `market 031.jpg`.

     ![Anzeigen von einem Datentipp](../debugger/media/dbg-tour-data-tips.gif "einem Datentipp anzeigen")

4. Erweitern Sie das Objekt, um alle Eigenschaften, wie etwa die `FullPath` Eigenschaft.

    Häufig beim Debuggen, möchten Sie eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte, und die Datentipps sind eine gute Möglichkeit zu diesem Zweck.

    > [!TIP]
    > In den meisten unterstützten Sprachen können Sie Code in der Mitte einer Debugsitzung bearbeiten, wenn Sie etwas finden, die Sie ändern möchten. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md). Um diese Funktion in dieser app verwenden, würden jedoch wir zuerst müssen die app-Version von .NET Framework aktualisieren.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Überprüfung von Variablen mit den Fenstern "Auto" und "lokal"

1. Betrachten Sie die **"Auto"** -Fensters am unteren Rand der Code-Editor.

     ![Prüfen Sie die Variablen im Fenster "Auto"](../debugger/media/dbg-tour-autos-window.png "Fenster "Auto"")

    In der **"Auto"** Fenster Variablen und der aktuelle Wert angezeigt. Die **"Auto"** Fenster enthält alle Variablen, die in der aktuellen Zeile oder die vorangehende Zeile verwendet wird (In C++ wird das Fenster zeigt Variablen in der vorhergehenden drei Codezeilen. In der Dokumentation für die sprachspezifisches Verhalten).

    > [!NOTE]
    > In JavaScript die **"lokal"** Fenster wird jedoch nicht unterstützt die **"Auto"** Fenster.

2. Betrachten Sie als Nächstes die **"lokal"** Fenster.

    Die **"lokal"** Fenster zeigt die Variablen, die sich im aktuellen Gültigkeitsbereich befinden.

    ![Prüfen Sie die Variablen im Fenster "lokal"](../debugger/media/dbg-tour-locals-window.png "Fenster "lokal"")

    Derzeit ist die `this` -Objekt und das Objekt "Datei" (`f`) befinden sich im aktuellen Gültigkeitsbereich. Weitere Informationen finden Sie unter [Untersuchen von Variablen im Fenster "lokal" und "Auto"](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Festlegen einer Überwachung

1. In der main-Code-Editor-Fenster mit der Maustaste das Objekt "Datei" (`f`), und wählen Sie **Überwachung hinzufügen**.

    Können Sie eine **Überwachen** Fenster auf angeben, eine Variable (oder ein Ausdruck), die Sie Auge behalten möchten.

    Jetzt haben Sie eine Überwachung, legen Sie für die `File` -Objekt, und Sie sehen den Wert ändern, wie Sie mithilfe des Debuggers verschieben. Im Gegensatz zu den anderen Variablenfenstern die **Überwachen** Fenster zeigt die Variablen immer, dass Sie beobachten sind (sie sind abgeblendet, wenn außerhalb des gültigen Bereichs).

2. Auf der `Add` -Methode, klicken Sie auf die grüne ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick") erneut (oder drücken Sie F11 einige Male) zum Fortsetzen der Verarbeitung der `foreach` Schleife.

    ![Legen Sie eine Überwachung auf eine Variable](../debugger/media/dbg-tour-watch-window.png "Fenster "überwachen"")

    Darüber hinaus möglicherweise das erste Bild, um das Hauptfenster der ausgeführten hinzugefügt werden Beispiel-app, aber dies erfolgt auf eine andere app-Thread, damit Bilder noch möglicherweise nicht sichtbar.

    Weitere Informationen finden Sie unter [legen Sie eine Überwachung mit der überwachen "und" Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Eine Ausnahme zu untersuchen

1. In der ausgeführten app-Fenster, löschen Sie den Text in der **Pfad** Eingabefeld und wählen Sie die **Änderung** Schaltfläche.

     ![Eine Ausnahme ausgelöst wird,](../debugger/media/dbg-tour-cause-an-exception.png "eine Ausnahme")

     Die Anwendung löst eine Ausnahme aus, und der Debugger gelangen Sie zu der Codezeile, die die Ausnahme ausgelöst hat.
     
     ![Ausnahmen-Hilfe](../debugger/media/dbg-tour-exception-helper.png "Ausnahmen-Hilfe")

     Hier wird die **Ausnahmen-Hilfe** erfahren Sie, eine `System.ArgumentException` und eine Fehlermeldung, die besagt, dass der Pfad nicht um ein ungültiges Format ist. Daher wissen, dass der Fehler aufgetreten ist, auf eine Methode oder Funktion-Argument.

     In diesem Beispiel wird die `DirectoryInfo` Aufruf der angegebene Fehler trat auf die leere Zeichenfolge, die in der `value` Variable. (Zeigen Sie auf `value` , finden in die leere Zeichenfolge.)

     Ausnahmen-Hilfe ist eine großartige Funktion, die Sie beim Debuggen von Fehlern helfen. Sie können auch Aktionen wie die Ansicht Fehlerdetails und Hinzufügen einer Überwachung von Ausnahmen-Hilfe. Oder, bei Bedarf können Sie Bedingungen für die bestimmte Ausnahme ändern.

    >  [!NOTE] 
    > Ausnahmen-Hilfe ersetzt der Ausnahmen-Assistent in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Erweitern Sie die **Ausnahmeeinstellungen** Knoten, um weitere Optionen zum Behandeln dieser Ausnahmetyp, aber Sie müssen nicht ändert nichts für diesen Überblick!

3. Drücken Sie F5, um die app zu fortfahren.

Weitere Informationen zu den Funktionen des Debuggers finden Sie unter [Debuggerdatentipps und Tricks](../debugger/debugger-tips-and-tricks.md).

## <a name="see-also"></a>Siehe auch

[Debuggen in Visual Studio](../debugger/index.md)  
[Debugger – Featuretour](../debugger/debugger-feature-tour.md)
