---
title: Lernen Sie das Debuggen mit Visual Studio-debugger
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303145"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Informationen Sie zum Debuggen mit Visual Studio

Dieses Thema führt die Funktionen von Visual Studio-Debugger in eine schrittweise exemplarische Vorgehensweise. Einen allgemeineren Überblick über die Funktionen des Debuggers, finden Sie unter [Debugger – Featuretour](../debugger/debugger-feature-tour.md). Wenn Sie *Debuggen Ihrer app*, er wird in der Regel bedeutet, dass Sie Ihre Anwendung mit dem angefügten Debugger ausgeführt werden. Wenn Sie dies tun, wird der Debugger bietet viele Möglichkeiten, um festzustellen, was den Status Ihres Codes während der Ausführung. Sie können den Code schrittweise durchlaufen und die Werte in Variablen gespeicherten, Sie können Überwachungen Variablen angezeigt, wenn die Werte ändern, können Sie den Ausführungspfad des Codes untersuchen Et al. Wenn dies das erste Mal, die Sie versucht haben ist, um Code zu debuggen, sollten Sie lesen [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md) vor dem Durcharbeiten dieses Themas.

Sie können entweder zusammen lesen, um die Funktionen des Debuggers finden Sie unter, oder Laden Sie das vollständige Beispiel, die in der Führung durch Features verwendet und führen Sie die Schritte selbst. Um das Beispiel herunterzuladen, und folgen zu können, finden Sie unter [Foto-Viewer-Demo](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) zum Debuggen, die ähnliche Schritte zeigt. |

Obwohl die Demo-app C# -Code ist, gelten die Funktionen, C++, Visual Basic, JavaScript und anderen Sprachen von Visual Studio (außer den) unterstützt.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten Sie den Debugger und Haltepunkte.
> * Erfahren Sie, Befehle aus, um Code im Debugger schrittweise durchlaufen
> * Überprüfen von Variablen in den Datentipps und Debugger-Fenster
> * Die Aufrufliste überprüfen
> * Verwenden Sie die Ausnahmen-Hilfe

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die. **NET Desktopentwicklung** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

    Falls Sie bereits über Visual Studio verfügen, aber die Workload noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** (**Datei** > **Neu** > **Projekt**) auf den Link **Visual Studio-Installer**. Der Visual Studio-Installer wird gestartet. Wählen Sie die. **NET Desktopentwicklung** Workload, wählen Sie dann **ändern**.

## <a name="start-the-debugger"></a>Starten Sie den Debugger an!

1. Um auf die folgenden Schritte in Visual Studio auszuführen, laden Sie das Beispiel [auf dieser Seite](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Installieren von Visual Studio mit der Workload ".NET Desktopentwicklung" zum Ausführen der app, die wir verwenden in der Demo werden sollen.

2. Entzippen Sie das Projekt aus.

3. Öffnen Sie Visual Studio, und wählen Sie die **Datei > Öffnen** Menü Befehl aus, und wählen Sie dann **Projekt/Projektmappe**, und öffnen Sie dann den Ordner, in dem Sie das Projekt heruntergeladen haben.

     ![Öffnen Sie das Beispielprojekt](../debugger/media/dbg-tour-open-project.png "Projekt öffnen")

3. Öffnen Sie die WPF-Foto-Viewer-Demo > C#-Ordner, wählen Sie die *photoapp.sln* , und wählen Sie **öffnen**.

     Das Projekt in Visual Studio wird geöffnet. Projektmappen-Explorer im rechten Bereich zeigt alle Projektdateien.

    ![Projektmappen-Explorer-Dateien](../debugger/media/dbg-tour-solution-explorer.png "Projektmappen-Explorer")

4. Drücken Sie **F5** (**Debuggen > Debuggen starten**) oder die **Debuggen starten** Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten ") in der Debug-Symbolleiste.

     ![Foto-Viewer-app](../debugger/media/dbg-tour-wpf-app.png "Foto-Viewer-App")

     F5 wird die app gestartet, mit dem Debugger an den app-Prozess, sondern angefügt werden, jetzt nicht getan haben wir keine Haltepunkte hinzugefügt oder erfolgt keine besonderen Untersuchung des Codes. Die app nur geladen, und die Foto-Images angezeigt.

     Bei dieser Führung durch wir werfen einen genaueren Blick auf dieser app, die mit dem Debugger und erhalten einen Blick auf die Debugger-Features.

5. Beenden Sie den Debugger durch Drücken der Beendigung des roten ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") Schaltfläche.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

Um zu debuggen, müssen Sie Ihre app mit dem an den app-Prozess angefügten Debugger zu starten.

1. In der `MainWindow` Konstruktor der "MainWindow.Xaml.cs" einen Haltepunkt festlegen, indem Sie auf den linken Rand der ersten Zeile des Codes.

     ![Festlegen eines Haltepunkts](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. 

6. Drücken Sie **F5** oder **Debuggen starten** Schaltfläche, die app gestartet wird, und der Debugger ausgeführt wird, um die Codezeile, in dem Sie den Haltepunkt gesetzt haben.

    Der gelbe Pfeil stellt die Anweisung auf der der Debugger angehalten ist, die auch app-Ausführung an der gleichen Stelle unterbricht (diese Anweisung wurde noch nicht ausgeführt).

    F5 wird das Ausführen der app bis zum nächsten Haltepunkt fortgesetzt. (Wenn die app noch nicht ausgeführt wird, F5 wird der Debugger gestartet und wird am ersten Haltepunkt angehalten.)

    Haltepunkte sind eine nützliche Funktion, wenn Sie wissen, die Zeile des Codes oder des Codeabschnitts, die Sie genauer untersuchen möchten.

## <a name="optional-restart-your-app-quickly"></a>(Optional) Starten Sie Ihre app schnell neu.

Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") der Debug-Symbolleiste (**STRG** + **UMSCHALT**   +  **F5**).

Beim Drücken **Neustart**, denn Sie spart Zeit und beenden die app und erneutes Starten des Debuggers. Der Debugger hält am ersten Haltepunkt, der erreicht wird, indem Sie Code ausführen.

Der Debugger hält wieder am Haltepunkt, in Festlegen der `MainWindow` Konstruktor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren Sie im Code im Debugger verwenden diese Befehle

In der Regel verwenden wir die Tastenkombinationen, da es sich um eine gute Möglichkeit, ist schnell auf Ihre app im Debugger (entsprechende Befehle z. B. Menü Befehle in Klammern angezeigt werden) ausführen.

1. Drücken Sie **F11** (**Debuggen > Einzelschritt**) zweimal, um die Ausführung der app, fahren Sie fort, die `InitializeComponent()` Funktion.

     ![Verwenden Sie F11, um Einzelschritt Code](../debugger/media/dbg-tour-f11.png "F11 Einzelschritt")

     F11 wird die **Einzelschritt** -Befehl aus, und setzt die app Ausführung einer Anweisung zu einem Zeitpunkt. F11 ist eine gute Möglichkeit, den Ausführungsablauf in die meisten Details zu überprüfen. (Um im Code schneller zu verschieben, zeigen wir Ihnen einige andere Optionen auch.) Standardmäßig überspringt der Debugger nicht benutzerseitiger Code (Sie weitere Informationen finden Sie unter [nur mein Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > In verwaltetem Code sehen Sie ein Dialogfeld gefragt, wenn Sie benachrichtigt werden, wenn Sie automatisch Eigenschaften und Operatoren überspringen (Standardverhalten) ausführen möchten. Wenn Sie die Einstellung ändern möchten später deaktivieren **Eigenschaften und Operatoren überspringen** festlegen in der **Tools > Optionen** Menü unter **Debuggen**.

2. Drücken Sie **F10** (**Debuggen > Prozedurschritt**) einige Male, bis der Debugger wird, in der ersten Zeile des Codes in angehalten der `OnApplicationStartup` -Ereignishandler.

     ![Verwenden Sie F10, um Prozedurschritt Code](../debugger/media/dbg-tour-f10-step-over.png "F10 Prozedurschritt")

     F10 wechselt den Debugger ohne einen Einzelschritt in die Funktionen oder Methoden in Ihrem app-Code (der Code wird immer noch ausgeführt). Durch Drücken von F10 auf die `InitializeComponent` Methodenaufruf (anstelle von F11), wir den Implementierungscode für übersprungen `InitializeComponent` (die vielleicht, es keine Sie jetzt möchten sind).

## <a name="step-into-a-property"></a>Einzelschritt in eine Eigenschaft

1. Mit der Debugger angehalten, auf diese Codezeile:

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Mit der rechten Maustaste auf die Codezeile, und wählen Sie **Einzelschritt in Angabe**, klicken Sie dann **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Verwenden Sie den Schritt in einer bestimmten Funktion](../debugger/media/dbg-tour-step-into-specific.png "Einzelschritt in Angabe")

    Erwähnt, wird standardmäßig der Debugger überspringt aus verwalteten Eigenschaften und Felder, aber die **Einzelschritt in Angabe** Befehl können Sie dieses Verhalten außer Kraft zu setzen. Jetzt möchten wir sehen, was geschieht, wenn die `Path.set` Eigenschaft-Setter ausgeführt wird. **Einzelschritt in Angabe** bringt uns zu den `Path.set` hier.

     ![Ergebnis der Einzelschritt in Angabe](../debugger/media/dbg-tour-step-into-specific-2.png "Einzelschritt in Angabe")

     Die `Update` -Methode in der dieser Code anscheinend sie möglicherweise interessant, lassen den Debugger verwenden, um diesen Code nah zu untersuchen.

5. Zeigen Sie auf die `Update` Methode, bis die grüne **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") auf der linken Seite angezeigt wird.

     ![Verwenden Sie die Ausführung bis Klick Feature](../debugger/media/dbg-tour-run-to-click-2.png "Ausführung bis Klick")

    >  [!NOTE]
    > Die **Ausführung bis Klick** Schaltfläche ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Wenn Sie nicht, dass die Schaltfläche mit dem grünen Pfeil sehen, verwenden Sie F11 in diesem Beispiel stattdessen um den Debugger zu gelangen.

6. Klicken Sie auf die **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mit dieser Schaltfläche ähnelt der als temporären Haltepunkt festlegen. **Ausführung bis Klick** ist praktisch für die Umgehung sich schnell innerhalb eines sichtbaren Bereichs des app-Codes (Sie können in einer geöffneten Datei klicken).

    Der Debugger setzt auf den `Update` methodenimplementierung.

7. Drücken Sie **F11** Einzelschritt auf dem `Update` Methode.

     ![Ergebnis der Update-Methode schrittweise](../debugger/media/dbg-tour-update-method.png "Schritt in Update-Methode")

    Hier finden wir einige weitere Code, der sieht interessant aus; die app erhält alle. *Jpg* -Dateien in einem bestimmten Verzeichnis befinden, und klicken Sie dann ein Foto-Objekt für jede Datei erstellt. Dieser Code bietet uns eine gute Gelegenheit, starten Sie den app-Status (Variablen) mit dem Debugger überprüfen. In den nächsten Abschnitten in diesem Tutorial werden wir dies.

    Funktionen, die Ihnen ermöglichen, Variablen untersuchen sind eines der nützlichsten Features des Debuggers, und es gibt verschiedene Möglichkeiten dafür. Häufig, wenn Sie versuchen, ein Problem debuggen können, sind Sie versucht, finden Sie heraus, ob Variablen die Werte speichern, die Sie zu einem bestimmten Zeitpunkt über erwarten.

## <a name="examine-the-call-stack"></a>Die Aufrufliste überprüfen

Bei angehaltener in die `Update` -Methode, klicken Sie auf die **Aufrufliste** Fenster, in dem wird standardmäßig in der unteren rechten Bereich geöffnet.

![Überprüfen Sie die Aufrufliste](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

Die **Aufrufliste** Fenster zeigt die Reihenfolge, in dem Methoden und Funktionen werden aufgerufen. Der obersten Zeile wird die aktuelle Funktion (der `Update` Methode in der Einführung in app). Die zweite Zeile zeigt, dass `Update` aufgerufen wurde, aus der `Path.set` -Eigenschaft, und So weiter.

>  [!NOTE]
> Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse.

Die Aufrufliste ist eine gute Möglichkeit zum Untersuchen und verstehen, den Ausführungsablauf der app.

Doppelklicken Sie auf eine einzige Zeile Code zu diesem Quellcode betrachten und ändert, die ebenfalls den aktuellen Bereich, der vom Debugger überprüft werden. Den Debugger weitergeführt diese Aktion nicht.

Sie können auch die Kontextmenüs von der **Aufrufliste** Fenster aus, um andere Dinge tun. Sie können z. B. Legen Sie Haltepunkte in der angegebenen Funktionen, fahren Sie fort mit **Ausführen bis Cursor**, und Untersuchen von Quellcode. Weitere Informationen finden Sie unter [Vorgehensweise: Untersuchen der Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Ausführen bis Rücksprung

Nehmen wir an, dass Sie fertig sind untersucht die `Update` -Methode in "Data.cs", und Sie möchten, nutzen Sie die Funktion, aber behalten Sie den Debugger. Hierzu können Sie mithilfe der **Ausführen bis Rücksprung** Befehl.

1. Drücken Sie **UMSCHALT** + **F11** (oder **Debuggen > Ausführen bis Rücksprung**).

     Mit diesem Befehl wird die app-Ausführung fortgesetzt (und den Debugger wechselt), bis die aktuelle Funktion zurückkehrt.

     Sie muss in der `Update` Methodenaufruf in "Data.cs".

2. Drücken Sie **UMSCHALT** + **F11** erneut, und der Debugger die Aufrufliste nach oben an den `OnApplicationStartup` -Ereignishandler.

## <a name="run-to-cursor"></a>Ausführen bis Cursor

1. Wählen Sie die **Debuggen beenden** rote Schaltfläche ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") oder **UMSCHALT** + **F5** .

2. In der `Update` -Methode in der *"Data.cs"*, mit der rechten Maustaste die `Add` Methodenaufruf, und wählen Sie **Ausführen bis Cursor**. Dieser Befehl startet das debugging und legt einen temporären Haltepunkt für die aktuelle Zeile des Codes.

     ![Verwenden Sie das Ausführen bis Cursor Feature](../debugger/media/dbg-tour-run-to-cursor.png "Ausführen bis Cursor")

    Sie sollten angehalten werden, an dem Haltepunkt in `MainWindow` (da dies der erste Haltepunkt ist festgelegt werden).

3. Drücken Sie **F5** , fahren Sie fort, um die `Add` , in denen ausgewählter **Ausführen bis Cursor**.

    Dieser Befehl ist nützlich, wenn Sie Code bearbeiten und schnell einen temporären Haltepunkt festlegen und den Debugger starten möchten.

## <a name="change-the-execution-flow"></a>Ändern Sie den Ausführungsablauf

1. Mit dem Debugger unterbrochen wird, auf die `Add` -Methodenaufruf, verwenden Sie die Maus auf der linken Seite den gelben Pfeil (der Ausführungszeiger) abrufen und verschieben Sie den gelben Pfeil, um eine Zeile, die `foreach` Schleife.

     ![Verschieben der Ausführungszeiger](../debugger/media/dbg-tour-move-the-execution-pointer.gif "der Ausführungszeiger verschieben")

    Ändern Sie den Ausführungsablauf, können Sie z. B. Ausführungspfade für anderen Code zu testen, oder führen Sie ohne Neustart des Debuggers den Code erneut ausführen.

2. Drücken Sie nun **F5**.

    Sie sehen, dass die Bilder, die das app-Fenster hinzugefügt. Da Sie Code erneut ausführen, werden die `foreach` Schleife, mit einigen der Images wurden zweimal hinzugefügt!

    > [!WARNING]
    > Häufig müssen Sie diese Funktion vorsichtig sein, und Sie wird eine Warnung in der QuickInfo angezeigt. Sie können andere Warnungen, zu sehen. Verschieben den Zeiger kann nicht rückgängig gemacht, Ihre Anwendung in einem früheren app-Status.

## <a name="inspect-variables-with-data-tips"></a>Untersuchen Sie Variablen mit den Datentipps

1. Open *"Data.cs"* der Foto-Viewer-Demo-app mit der Maustaste der `private void Update` Funktionsdeklaration, und wählen Sie **Ausführen bis Cursor** (beendet die app zuerst, wenn er bereits ausgeführt wird).

    Dadurch wird die app mit dem angefügten Debugger angehalten. Dadurch können wir den Zustand zu untersuchen.

2. Zeigen Sie auf die `Add` Methodenaufruf, und klicken Sie auf die **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Zeigen Sie es jetzt auf das Objekt "Datei" (`f`), und Sie sehen, dass der Standardwert der Eigenschaft, den Dateinamen *Markt 031. Jpg*.

     ![Anzeigen ein Datentipps](../debugger/media/dbg-tour-data-tips.gif "einem Datentipp anzeigen")

4. Erweitern Sie das Objekt, um alle zugehörigen Eigenschaften, z. B. finden Sie unter den `FullPath` Eigenschaft.

    Häufig, wenn Debuggen, sollten Sie eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte, und der Datentipps sind eine gute Möglichkeit dafür.

    > [!TIP]
    > Die meisten unterstützten Sprachen können Sie Code in der Mitte einer Debugsitzung bearbeiten, wenn Sie etwas finden, die Sie ändern möchten. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md). Um dieses Feature in dieser app zu verwenden, würde jedoch müssen wir zuerst auf der app-Version von .NET Framework zu aktualisieren.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen Sie Variablen mit den Fenstern "Auto" und "lokal"

1. Sehen Sie sich die **"Auto"** Fenster am unteren Rand der Code-Editor.

     ![Untersuchen Sie Variablen im Fenster "Auto"](../debugger/media/dbg-tour-autos-window.png "Fenster \"Auto\"")

    In der **"Auto"** Fenster Variablen und ihren aktuellen Wert angezeigt. Die **"Auto"** Fenster zeigt alle Variablen, die in der aktuellen Zeile oder die vorangehende Zeile verwendet wird (In C++ wird das Fenster zeigt Variablen in den vorherigen drei Zeilen des Codes. Dokumentation für die sprachspezifisches Verhalten).

    > [!NOTE]
    > In JavaScript die **"lokal"** Fenster wird nicht unterstützt die **"Auto"** Fenster.

2. Betrachten Sie als Nächstes die **"lokal"** Fenster.

    Die **"lokal"** Fenster zeigt die Variablen, die im aktuellen Gültigkeitsbereich sind.

    ![Untersuchen Sie Variablen im Fenster "lokal"](../debugger/media/dbg-tour-locals-window.png "Fenster \"lokal\"")

    Derzeit den `this` -Objekt und das Objekt "Datei" (`f`) befinden sich im aktuellen Gültigkeitsbereich. Weitere Informationen finden Sie unter [Überprüfen von Variablen in der "Auto" und "lokal" Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Set a Watch festlegen

1. Maustaste Sie im Hauptmenü Code-Editor-Fenster, das Objekt "Datei" (`f`), und wählen Sie **Überwachung hinzufügen**.

    Können Sie eine **Watch** Fenster, geben auf eine Variable (oder eines Ausdrucks), die Sie im Auge zu behalten möchten.

    Nun müssen Sie eine Überwachung, legen Sie für die `File` -Objekt, und Sie sehen den Wert ändern, wie Sie den Debugger verschieben. Im Gegensatz zu anderen Variablenfenstern die **Watch** Fenster enthält stets den Variablen, die Sie überwachen (sie sind ausgegraut, wenn außerhalb des gültigen Bereichs).

2. Auf der `Add` -Methode, klicken Sie auf die grüne ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") erneut aus (oder drücken Sie F11, einige Male), fahren Sie fort, über die `foreach` Schleife.

    ![Festlegen eines überwachungselements für eine Variable](../debugger/media/dbg-tour-watch-window.png "Fenster \"überwachen\"")

    Sie können auch sehen, das erste Bild im Hauptfenster der ausgeführten hinzugefügt werden Beispiel-app, aber dies geschieht in einem anderen app-Thread, damit Bilder nicht noch sichtbar sein können.

    Weitere Informationen finden Sie unter [festlegen eine Überwachung mit dem überwachen und Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Untersuchen einer Ausnahme

1. In der ausgeführten app-Fenster, löschen Sie den Text in die **Pfad** Feld "Eingabe", und wählen die **Änderung** Schaltfläche.

     ![Eine Ausnahme ausgelöst wird](../debugger/media/dbg-tour-cause-an-exception.png "dazu führen, dass eine Ausnahme")

     Die app löst eine Ausnahme aus, und der Debugger gelangen Sie zu der Codezeile, die die Ausnahme ausgelöst hat.

     ![Ausnahmen-Hilfe](../debugger/media/dbg-tour-exception-helper.png "Ausnahmen-Hilfe")

     Hier die **Ausnahmehilfsprogramm** erfahren Sie, eine `System.ArgumentException` und eine Fehlermeldung, die besagt, dass der Pfad kein ungültiges Format. Wir wissen also, dass der Fehler aufgetreten ist, auf eine Methode oder Funktion-Argument.

     In diesem Beispiel die `DirectoryInfo` Aufruf hat den Fehler, auf die leere Zeichenfolge, die in der `value` Variable. (Zeigen Sie auf `value` die leere Zeichenfolge angezeigt.)

     Die Ausnahmen-Hilfe ist eine großartige Funktion, die Sie das Debuggen von Fehlern unterstützen. Sie können auch Dinge wie Ansicht Fehlerdetails und Hinzufügen einer Überwachung aus der Ausnahme-Hilfe. Oder, bei Bedarf können Sie Bedingungen für eine bestimmte Ausnahme ändern.

    >  [!NOTE]
    > Die Ausnahmen-Hilfe, ersetzt der Ausnahmen-Assistent in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Erweitern Sie die **Ausnahmeeinstellungen** Knoten finden weitere Möglichkeiten zum Behandeln dieser Ausnahmetyp, aber Sie müssen nicht alles für diesen Überblick zu ändern.

3. Drücken Sie **F5**, um die App fortzusetzen.

Weitere Informationen zu den Funktionen des Debuggers finden Sie unter [Debugger Tipps und Tricks](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und untersuchen Sie Variablen. Sie sollten einen allgemeinen Überblick über die Debugger-Features sowie Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
