---
title: 'Tutorial: Debuggen von Visual Basic-Code'
description: Erfahren Sie, wie Sie den Visual Studio-Debugger starten, den Code durchlaufen und Daten überprüfen.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6033ce2329974cc3c2b1f140d02d112e4f87ba9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985837"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Tutorial: Informationen zum Debuggen von Visual Basic-Code mit Visual Studio

In diesem Artikel werden die Funktionen des Visual Studio-Debuggers in einer ausführlichen exemplarischen Vorgehensweise vorgestellt. Einen allgemeineren Überblick über die Funktionen des Debuggers finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../../debugger/debugger-feature-tour.md). Wenn Sie *Ihre App debuggen*, bedeutet dies in der Regel, dass Sie Ihre Anwendung mit dem angefügten Debugger ausführen. Wenn Sie dies machen, bietet der Debugger viele Möglichkeiten zum Ermitteln des Status Ihres Codes während der Ausführung. Sie können Ihren Code schrittweise durchlaufen und die Werte prüfen, die in Variablen gespeichert sind, Sie können die Überwachung von Variablen festlegen, um zu sehen, wenn sich Werte ändern, und Sie können den Ausführungspfad Ihres Codes prüfen und feststellen, ob ein Codezweig ausgeführt wird usw. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../../debugger/debugging-absolute-beginners.md) lesen, bevor Sie diesen Artikel durchgehen.

| | |
|---------|---------|
| ![Kamerasymbol für Video](../../install/media/video-icon.png "Video ansehen") | Zum Debuggen können Sie sich ein [Video ansehen](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171), in dem ähnliche Schritte beschrieben werden. |

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Debuggers und Treffen der Breakpoints.
> * Erlernen von Befehlen zum Durchlaufen des Codes im Debugger
> * Überprüfen von Variablen im Fenster für Datentipps und im Debugger-Fenster
> * Überprüfen der Aufrufliste

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 und die Workload für die **.NET-Desktopentwicklung** installiert haben.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  kostenlos herunterladen.

    Falls Sie bereits über Visual Studio verfügen, aber die Workload noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** (**Datei** > **Neu** > **Projekt**) auf den Link **Visual Studio-Installer**. Der Visual Studio-Installer wird gestartet. Wählen Sie beispielsweise die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual Basic** auf **Windows-Desktop** und dann im mittleren Bereich auf **Konsolen-App**.

    Wenn Ihnen die Projektvorlage **Konsolenanwendung** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload *.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.

3. Geben Sie einen Namen ein, z.B. **get-gestartet-debugging**, und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. Ersetzen Sie in *Program.cs* den folgenden Code:

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    durch den folgenden:

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Starten Sie den Debugger.

1. Drücken Sie die Taste **F5** (**Debuggen > Debuggen starten**), oder klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten** ![Debuggen starten](../../debugger/media/dbg-tour-start-debugging.png "Start Debugging").

     Durch Drücken der Taste **F5** wird die App mit dem an den App-Prozess angefügten Debugger gestartet. Bisher haben Sie jedoch nichts weiter gemacht, um den Code zu untersuchen. Die App wird lediglich geladen, und Ihnen wird die Konsolenausgabe angezeigt.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In diesem Tutorial werfen wir einen genaueren Blick auf diese App mit dem Debugger und schauen uns die Funktionen des Debuggers an.

2. Durch Drücken der roten Stopptaste ![Debuggen beenden](../../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") können Sie den Debugger beenden.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Breakpoints und Starten des Debuggers

1. Legen Sie in der `For Each`-Schleife der Funktion `Main` einen Breakpoint fest, indem Sie auf den linken Rand der folgenden Codezeile klicken:

    `shape.Draw()`

    An der Stelle des Haltepunkts wird ein roter Kreis angezeigt.

    ![Haltepunkt festlegen](../visual-basic/media/get-started-set-breakpoint-vb.png)

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

2. Drücken Sie **F5**, oder klicken Sie auf die Schaltfläche**Debuggen starten** ![Debuggen starten](../../debugger/media/dbg-tour-start-debugging.png "Debuggen starten"). Daraufhin wird die App gestartet, und der Debugger führt den Code bis zu der Codezeile aus, in der Sie den Breakpoint festgelegt haben.

    ![Treffen eines Haltepunkts](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Der gelbe Pfeil stellt die Anweisung dar, an der der Debugger angehalten hat. An der gleichen Stelle wird auch die Ausführung der App unterbrochen (diese Anweisung wurde noch nicht ausgeführt).

     Wenn die App noch nicht ausgeführt wird, kann der Debugger durch Drücken der Taste **F5** gestartet werden und hält am ersten Haltepunkt an. Andernfalls wird durch Drücken der Taste **F5** die Ausführung der App bis zum nächsten Haltepunkt fortgesetzt.

    Haltepunkte sind eine nützliche Funktion, wenn Ihnen die Codezeile oder der Codeabschnitt bekannt ist, die bzw. den Sie genauer untersuchen möchten.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren durch Code im Debugger mithilfe von Schrittbefehlen

In der Regel verwenden wir an dieser Stelle Tastenkombinationen, da auf diese Weise eine schnelle Ausführung Ihrer App im Debugger möglich ist (entsprechende Befehle, wie z.B. Menübefehle, werden in Klammern angezeigt).

1. Drücken Sie, während der `shape.Draw`-Methodenaufruf in der `Main`-Funktion angehalten wurde, die Taste **F11** (oder klicken Sie auf **Debuggen > Schrittweise ausführen**), um den Code für die `Rectangle`-Klasse anzuzeigen.

     ![Verwenden von F11 für schrittweise Codeausführung](../visual-basic/media/get-started-f11-vb.png "F11: Schrittweise ausführen")

     Durch Drücken der Taste F11 wird der Befehl **Schrittweise ausführen** gesendet und die App Anweisung für Anweisung ausgeführt. Das Drücken der Taste F11 bietet eine gute Möglichkeit, den Ausführungsablauf am ausführlichsten zu überprüfen. (Wenn Sie den Code schneller durchlaufen möchten, zeigen wir Ihnen auch einige andere Optionen.) Standardmäßig überspringt der Debugger Nichtbenutzercode (weitere Einzelheiten hierzu finden Sie unter [Nur eigenen Code](../../debugger/just-my-code.md)).

2. Drücken Sie so lange die Taste **F10** (oder klicken Sie auf **Debuggen > Step Over (Überspringen)**), bis der Debugger beim `MyBase.Draw`-Methodenaufruf anhält. Drücken Sie anschließend erneut die Taste **F10**.

     ![Verwenden von F10 zum Überspringen von Code](../visual-basic/media/get-started-step-over-vb.png "F10 – Überspringen")

     Beachten Sie, dass der Debugger die `Draw`-Methode der Basisklasse (`Shape`) dieses Mal nicht schrittweise ausführt. Durch Drücken der Taste **F10** fährt der Debugger in Ihrem App-Code fort, ohne dass Funktionen oder Methoden schrittweise ausgeführt werden (der Code wird immer noch ausgeführt). Durch Drücken von **F10** im `MyBase.Draw`-Methodenaufruf (anstelle von **F11**) wurde der Implementierungscode für `MyBase.Draw` übersprungen (der für uns gerade möglicherweise nicht von Interesse ist).

## <a name="navigate-code-using-run-to-click"></a>Navigieren durch Code mithilfe von „Ausführung bis Klick“

1. Scrollen Sie im Code-Editor nach unten und bewegen Sie den Cursor so lange über die `Console.WriteLine`-Methode in der `Triangle`-Klasse, bis auf der linken Seite die grüne Schaltfläche **Ausführung bis Klick** ![Ausführung bis Klick](../../debugger/media/dbg-tour-run-to-click.png "Ausführung bis Klick") angezeigt wird. Die QuickInfo für die Schaltfläche zeigt „Ausführung bis hier ausführen“ an.

     ![Verwenden der Funktion „Ausführung bis Klick“](../visual-basic/media/get-started-run-to-click-vb.png "Ausführung bis Klick")

   > [!NOTE]
   > Die Schaltfläche **Ausführung bis Klick** ist neu in [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Wenn Ihnen die Schaltfläche mit dem grünen Pfeil nicht angezeigt wird, verwenden Sie in diesem Beispiel stattdessen die Taste **F11**, damit der Debugger an der richtigen Stelle fortfährt.

2. Klicken Sie auf die Schaltfläche **Ausführung bis Klick** ![Ausführung bis Klick](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Die Verwendung dieser Schaltfläche ist vergleichbar mit dem Festlegen eines temporären Haltepunkts. **Ausführung bis Klick** ist praktisch, um schnell durch einen sichtbaren Bereich mit App-Code zu navigieren (Sie können in eine beliebige geöffnete Datei klicken).

    Der Debugger fährt bis zur Implementierung der `Console.WriteLine`-Methode für die `Triangle`-Klasse fort.

    Nach dem Anhalten des Debuggers fällt Ihnen ein Tippfehler auf. Die Ausgabe "Drawing a trangle" ist falsch geschrieben. Dieser Fehler kann direkt hier korrigiert werden, während die App im Debugger ausgeführt wird.

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

1. Klicken Sie auf "Drawing a trangle", und ersetzen Sie „trangle“ durch „triangle“.

1. Drücken Sie **F11** einmal, und der Debugger wird weiter ausgeführt.

    > [!NOTE]
    > Abhängig vom Codetyp, den Sie im Debugger bearbeiten, wird Ihnen möglicherweise eine Warnmeldung angezeigt. In einigen Szenarios muss der Code erneut kompilieren, bevor Sie fortfahren können.

## <a name="step-out"></a>Ausführen bis Rücksprung

Angenommen Sie haben die `Draw`-Methode in der `Triangle`-Klasse fertig untersucht und möchten die Funktion, aber nicht den Debugger, beenden. Dies ist mit dem Befehl **Ausführen bis Rücksprung** möglich.

1. Drücken Sie **UMSCHALT** + **F11** (oder klicken Sie auf **Debuggen > Ausführen bis Rücksprung**).

     Mit diesem Befehl wird die Ausführung der App so lange fortgesetzt (und der Debugger weiter ausgeführt), bis die aktuelle Funktion wieder ausgeführt wird.

     Jetzt sollten Sie sich wieder in der `For Each`-Schleife in der `Main`-Methode befinden.

## <a name="restart-your-app-quickly"></a>Schnelles Neustarten Ihrer App

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

Durch das Klicken auf **Neu starten** sparen Sie im Vergleich zum Beenden der App und dem erneuten Starten des Debuggers Zeit. Der Debugger hält am ersten Breakpoint an, der bei der Codeausführung erreicht wird.

Der Debugger hält erneut an dem von Ihnen festgelegten Breakpoint an, bei der `shape.Draw()`-Methode.

## <a name="inspect-variables-with-data-tips"></a>Untersuchen von Variablen mithilfe von Datentipps

Funktionen, mit denen Sie Variablen untersuchen können, zählen zu den nützlichsten Funktionen des Debuggers. Es gibt verschiedene Möglichkeiten, Variablen zu untersuchen. Beim Debuggen eines Problems wird häufig versucht herauszufinden, ob Variablen die Werte speichern, die diese zu einem bestimmten Zeitpunkt erwartungsgemäß aufweisen.

1. Während der Debugger bei der `shape.Draw()`-Methode anhält und Sie den Cursor über das Objekt `shapes` bewegen, wird Ihnen der zugehörige Standardeigenschaftswert, die Eigenschaft `Count`, angezeigt.

1. Erweitern Sie das Objekt `shapes`, um sämtliche zugehörige Eigenschaften anzuzeigen, wie z. B. den ersten Index des Arrays `[0]` mit dem Wert `Rectangle`.

     ![Anzeigen eines Datentipps](../visual-basic/media/get-started-data-tip-vb.png "View a Data Tip")

    Sie können Objekte weiter erweitern, um die zugehörigen Eigenschaften anzuzeigen, wie z.B. die Eigenschaft `Height` des Rechtecks.

    Beim Debuggen möchten Sie häufig eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte. Die Datentipps stellen eine gute Methode hierfür dar.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen von Variablen über die Fenster „Auto“ und „Lokal“

1. Schauen Sie sich das Fenster **Auto** unten im Code-Editor an.

     ![Untersuchen von Variablen im Fenster „Auto“](../visual-basic/media/get-started-autos-window-vb.png "Fenster „Auto“")

    Im Fenster **Auto** werden Ihnen Variablen und der zugehörige aktuelle Wert angezeigt. Im **Auto**-Fenster werden alle Variablen angezeigt, die auf der aktuellen Zeile oder der vorangehenden Zeile verwendet werden (lesen Sie dazu die Dokumentation für sprachspezifisches Verhalten).

2. Schauen Sie sich als Nächstes das Fenster **Lokal** auf einer Registerkarte neben dem Fenster **Auto** an.

    Im Fenster **Lokal** werden Ihnen die Variablen angezeigt, die sich im aktuellen [Bereich](https://www.wikipedia.org/wiki/Scope_(computer_science)) befinden, also im aktuellen Ausführungskontext.

## <a name="set-a-watch"></a>Festlegen von Überwachung

1. Klicken Sie im Hauptfenster des Code-Editors mit der rechten Maustaste auf das Objekt `shapes`, und wählen Sie **Überwachung hinzufügen** aus.

    Das Fenster **Überwachung** wird unten im Code-Editor geöffnet. Sie können über das Fenster **Überwachung** eine Variable (oder einen Ausdruck) angeben, die Sie im Auge behalten möchten.

    Nun haben Sie festgelegt, dass das Objekt `shapes` überwacht werden soll, und Sie können seine Wertänderung sehen, wenn Sie durch den Debugger navigieren. Im Gegensatz zu den anderen Variablenfenstern werden im Fenster **Überwachung** immer die Variablen angezeigt, die von Ihnen überwacht werden (wenn sie außerhalb des gültigen Bereichs liegen, sind sie ausgegraut).

## <a name="examine-the-call-stack"></a>Überprüfen der Aufrufliste

1. Klicken Sie, nachdem in der `For Each`-Schleife angehalten wurde, auf das Fenster **Aufrufliste**. Dieses Fenster ist standardmäßig im unteren rechten Bereich geöffnet.

2. Drücken Sie einige Male die Taste **F11**, bis der Debugger bei der `MyBase.Draw`-Methode der Klasse `Rectangle` im Code-Editor anhält. Schauen Sie sich das Fenster **Aufrufliste** an.

    ![Überprüfen der Aufrufliste](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. In der obersten Zeile wird die aktuelle Funktion (in dieser App die `Rectangle.Draw`-Methode) angezeigt. In der zweiten Zeile wird angezeigt, dass `Rectangle.Draw` über die `Main`-Funktion aufgerufen wurde usw.

   > [!NOTE]
   > Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

    Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

    Sie können auf eine Codezeile doppelklicken, um diesen Quellcode anzuzeigen. Dadurch wird auch der aktuelle Bereich geändert, der vom Debugger untersucht wird. Durch diese Aktion wird der Debugger nicht weiter ausgeführt.

    Sie können auch über die Kontextmenüs im Fenster **Aufrufliste** weitere Aktionen ausführen. So können Sie beispielsweise Haltepunkte in bestimmte Funktionen einfügen, den Debugger über **Ausführen bis Cursor** weiter ausführen und Quellcode untersuchen. Weitere Informationen finden Sie unter [View the call stack and use the Call Stack window in the debugger Examine the Call Stack (Vorgehensweise: Untersuchen der Aufrufliste)](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

1. Wenn der Debugger im Methodenaufruf `MyBase.Draw` der Klasse `Rectangle` angehalten wurde, ziehen Sie den gelben Pfeil (den Ausführungszeiger) mit der Maus nach links und um eine Zeile nach oben in den `Console.WriteLine`-Methodenaufruf.

1. Drücken Sie die Taste **F11**.

    Der Debugger führt die `Console.WriteLine`-Methode erneut aus (die doppelte Ausgabe wird im Konsolenfenster angezeigt).

    Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

    > [!WARNING]
    > Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Durch das Verschieben des Zeigers können Sie Ihre Anwendung nicht auf einen früheren App-Status zurücksetzen.

1. Drücken Sie die Taste **F5**, um die Ausführung der App fortzusetzen.

    Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../../debugger/debugger-feature-tour.md)
