---
title: Weitere Informationen zum Debuggen von Multithreadanwendungen
description: Debuggen mithilfe paralleler Stapel und paralleler Überwachungs Fenster in Visual Studio
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e21d5174c9a909e9ad8031dfb7585abc52a7e78
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091794"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Einstieg in das Debuggen vonC#Multithreadanwendungen C++(, Visual Basic,)

Visual Studio bietet verschiedene Tools und Benutzeroberflächen Elemente, die Sie beim Debuggen von Multithreadanwendungen unterstützen. In diesem Tutorial wird gezeigt, wie Thread Marker, das Fenster **parallele Stapel** , das **parallele Überwachungs** Fenster, bedingte Haltepunkte und Filter Breakpoints verwendet werden. In diesem Tutorial erfahren Sie mehr über die Visual Studio-Funktionen zum Debuggen von Multithreadanwendungen.

Diese beiden Themen enthalten zusätzliche Informationen zur Verwendung anderer Multithread-Debuggingtools:

- Informationen zum Verwenden der Symbolleiste **Debugspeicherort** und des Fensters **Threads** finden Sie unter Exemplarische Vorgehensweise [: Debuggen einer Multithreadanwendung](../debugger/how-to-use-the-threads-window.md)

- Ein Beispiel für die Verwendung von <xref:System.Threading.Tasks.Task> (verwalteter Code) und der ParallelitätsC++Laufzeit () finden Sie unter Exemplarische Vorgehensweise [: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md). Allgemeine Tipps zum Debuggen, die für die meisten Multithread-Anwendungs Typen gelten, finden Sie in diesem Thema und in diesem Thema.

Sie benötigen zunächst ein Multithread-Anwendungsprojekt. Ein Beispiel folgt.

## <a name="create-a-multithreaded-app-project"></a>Erstellen eines Multithread-App-Projekts

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

   ::: moniker range=">=vs-2019"

   Wenn das Startfenster nicht geöffnet ist, wählen Sie **Datei** > **Fenster Start**aus.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie **C#** als nächstes **C++** , oder **Visual Basic** aus der Liste Sprache aus, und wählen Sie dann in der Liste Plattform die Option **Windows** aus. 

   Nachdem Sie die Sprach-und Platt Form Filter angewendet haben, wählen Sie die **Konsolen-app (.net Core)** oder für Konsolen- C++ **App** -Vorlage aus, und klicken Sie dann auf **weiter**.

   > [!NOTE]
   > Wenn die richtige Vorlage nicht angezeigt **wird, navigieren Sie zu Extras** > **Tools und Features anzeigen...** , um die Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung*** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname den Namen** " *mythleswalkyghapp* " ein, oder geben Sie ihn ein. Wählen Sie anschließend **Erstellen** aus.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialog Felds **Neues Projekt** die folgenden Optionen aus:

   - Wählen Sie C# für eine-APP unter **Visual C#** den **Windows-Desktop**aus, und wählen Sie dann im mittleren Bereich die Option **Konsolen-app (.NET Framework)** aus.
   - Wählen Sie für eine Visual Basic-app unter **Visual Basic**die Option **Windows-Desktop**aus, und wählen Sie dann im mittleren Bereich die Option **Konsolen-app (.NET Framework)** aus.
   - Wählen Sie C++ für eine-APP unter **Visual C++** den **Windows-Desktop**aus, und wählen Sie dann **Windows-Konsolenanwendung**aus.

   Wenn Sie die Konsolen- **app (.net Core)** oder C++für die **Konsolen-App** -Projektvorlage nicht sehen, wechseln **Sie zu Extras** > **Tools und Features anzeigen...** , um die Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung*** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie dann einen Namen wie " *mythleswalkyghapp* " ein, und klicken Sie auf **OK**.

   Klicken Sie auf **OK**.
   ::: moniker-end

   Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der Sprache, die Sie ausgewählt haben, kann die Quelldatei " *Program.cs*", " *mythleswalkyghapp. cpp*" oder " *Module1. vb*" genannt werden.

1. Löschen Sie den Code, der in der Quelldatei angezeigt wird, und ersetzen Sie ihn durch das unten aufgeführte Beispiel Codelisting.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended. " + data);
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended. " + data)
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. Wählen Sie im Menü **Datei** den Befehl **Alle speichern** aus.

1. (Nur Visual Basic) Klicken Sie in Projektmappen-Explorer (rechter Bereich) mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Ändern Sie auf der Registerkarte **Anwendung** das **Start Objekt** in **einfach**.

## <a name="debug-the-multithreaded-app"></a>Debuggen der Multithread-App

1. Suchen Sie im Quellcode-Editor nach einem der folgenden Code Ausschnitte:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Klicken Sie mit der linken Maustaste auf den linken bundplatz der Anweisung `Thread.Sleep` oder `std::this_thread::sleep_for`, um einen neuen Haltepunkt einzufügen.

    Im bundbundbereich gibt ein roter Kreis an, dass an dieser Stelle ein Haltepunkt festgelegt wird.

2. Wählen Sie im Menü **Debuggen** die Option **Debuggen starten** (**F5**) aus.

    Visual Studio erstellt die Projekt Mappe, die APP beginnt mit dem Anfügen des Debuggers, und die APP wird am Haltepunkt angehalten.

3. Suchen Sie im Quellcode-Editor die Zeile, die den Breakpoint enthält.

### <a name="ShowThreadsInSource"></a>Thread Marker ermitteln  

1. Wählen Sie auf der Symbolleiste Debuggen die Schaltfläche **Threads in Quelle anzeigen** , ![Threads in Quelle](../debugger/media/dbg-multithreaded-show-threads.png "Threadmarker")anzeigen aus.

2. Drücken Sie die Taste **F11** , um den Debugger eine Codezeile zu verschieben.

3. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile *wird ein Thread* ![Markierungs](../debugger/media/dbg-thread-marker.png "Threadmarker") Symbol Thread Marker angezeigt, der zwei gedrehten Threads ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Ein Thread Marker kann teilweise durch einen Haltepunkt verborgen werden.

4. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt, der den Namen und die Thread-ID für jeden beendeten Thread anzeigt. In diesem Fall ist der Name wahrscheinlich `<noname>`.

5. Wählen Sie den Thread Marker aus, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

### <a name="ParallelStacks"></a>Anzeigen der Thread Speicherorte

Im Fenster **parallele Stapel** können Sie zwischen einer Thread Ansicht und der Aufgaben Ansicht (für aufgabenbasierte Programmierung) wechseln, und Sie können Aufruf Listen Informationen für jeden Thread anzeigen. In dieser APP können wir die Thread Ansicht verwenden.

1. Öffnen Sie das Fenster **parallele Stapel** , indem Sie > **Fenster** > **parallele Stapel** **Debuggen** auswählen. Es sollte etwas ähnlich dem folgenden angezeigt werden. Die genauen Informationen unterscheiden sich je nach dem aktuellen Speicherort der einzelnen Threads, der Hardware und der Programmiersprache.

    ![Fenster "parallele Stapel"](../debugger/media/dbg-multithreaded-parallel-stacks.png "Parallelstackswindow")

    In diesem Beispiel sehen Sie von links nach rechts diese Informationen für verwalteten Code:

    - Der Haupt Thread (auf der linken Seite) wurde am `Thread.Start`beendet, wobei der Endpunkt durch das Thread Marker-Symbol ![Thread Marker](../debugger/media/dbg-thread-marker.png "Threadmarker")gekennzeichnet wird.
    - Zwei Threads haben die `ServerClass.InstanceMethod`eingegeben, von denen einer der aktuelle Thread (gelber Pfeil) ist, während der andere Thread in `Thread.Sleep`angehalten wurde.
    - Ein neuer Thread (auf der rechten Seite) wird ebenfalls gestartet, aber auf `ThreadHelper.ThreadStart`angehalten.

2. Klicken Sie mit der rechten Maustaste auf Einträge im Fenster **parallele Stapel** , um die verfügbaren Optionen im Kontextmenü anzuzeigen.

    Sie können in diesen Kontextmenüs verschiedene Aktionen durchführen. in diesem Tutorial zeigen wir jedoch weitere Informationen im Fenster **parallele Überwachung** (nächste Abschnitte).

    > [!NOTE]
    > Verwenden Sie stattdessen das Fenster **Threads** , um eine Listenansicht mit Informationen zu jedem Thread anzuzeigen. Siehe Exemplarische Vorgehensweise [: Debuggen einer Multithread-Anwendung](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Festlegen einer Überwachung für eine Variable

1. Öffnen Sie das Fenster **parallele Überwachung** , indem Sie **Debuggen** > **Fenster** > **parallele Überwachung** > **parallele Überwachung 1**auswählen.

2. Wählen Sie die Zelle aus, in der der `<Add Watch>` Text (oder die leere Header Zelle in der 4. Spalte) angezeigt wird, und geben Sie `data`ein.

    Die Werte für die Daten Variable für jeden Thread werden im-Fenster angezeigt.

3. Wählen Sie die Zelle aus, in der der `<Add Watch>` Text (oder die leere Header Zelle in der 5. Spalte) angezeigt wird, und geben Sie `count`ein.

    Die Werte für die `count` Variable für jeden Thread werden im-Fenster angezeigt. Wenn diese Informationen noch nicht angezeigt werden, versuchen Sie, **F11** mehrmals zu drücken, um die Ausführung der Threads im Debugger voranzubringen.

    ![Fenster für parallele Überwachung](../debugger/media/dbg-multithreaded-parallel-watch.png "Parallelwatchwindow")

4. Klicken Sie mit der rechten Maustaste auf eine der Zeilen im-Fenster, um die verfügbaren Optionen anzuzeigen.

### <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung
Sie können Threads markieren, um wichtige Threads nachzuverfolgen und die anderen Threads zu ignorieren.

1. Halten Sie im Fenster **parallele Überwachung** die **UMSCHALT** Taste gedrückt, und wählen Sie mehrere Zeilen aus.

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **Flag**.

    Alle ausgewählten Threads werden gekennzeichnet. Nun können Sie filtern, um nur gekennzeichnete Threads anzuzeigen.

3. Wählen Sie im Fenster **parallele Überwachung** ![die Schaltfläche](../debugger/media/dbg-threads-show-flagged.png "Threadmarker")nur gekennzeichnete **Threads anzeigen** aus.

    Nur die gekennzeichneten Threads werden in der Liste angezeigt.

    > [!TIP]
    > Nachdem Sie einige Threads gekennzeichnet haben, können Sie im Code-Editor mit der rechten Maustaste auf eine Codezeile klicken und die Option **markierte Threads zum Cursor ausführen**auswählen. Stellen Sie sicher, dass Sie Code auswählen, der von allen markierten Threads erreicht wird. Visual Studio hält Threads in der ausgewählten Codezeile an, sodass die Ausführungsreihenfolge einfacher gesteuert werden kann, indem [Threads eingefroren und](#bkmk_freeze)aktiviert werden.

4. Wählen Sie die Schaltfläche nur gekennzeichnete **Threads anzeigen** erneut aus, um zurück zum Modus **alle Threads anzeigen** zu wechseln.

5. Klicken Sie zum Aufheben der Kennzeichnung von Threads mit der rechten Maustaste auf einen oder mehrere gekennzeichnete Threads im Fenster **parallele Überwachung** , **und wählen Sie**Kennzeichnung aufheben aus.

### <a name="bkmk_freeze"></a>Einfrieren der Thread Ausführung

> [!TIP]
> Sie können Threads fixieren und wieder aufnehmen (angehalten und fortsetzen), um die Reihenfolge zu steuern, in der die Threads Arbeit ausführen. Dies kann Ihnen dabei helfen, Parallelitäts Probleme wie Deadlocks und Racebedingungen zu beheben.

1. Klicken Sie im Fenster **parallele Überwachung** mit der rechten Maustaste, und wählen Sie **Einfrieren**aus.

    In der zweiten Spalte wird für jede Zeile ein Pausen Symbol angezeigt. Das Pausen Symbol gibt an, dass der Thread eingefroren ist.

2. Deaktivieren Sie alle anderen Zeilen, indem Sie nur eine Zeile auswählen.

3. Klicken Sie mit der rechten Maustaste auf eine Zeile, und wählen Sie **Thaw**

    Das Pausen Symbol läuft in dieser Zeile ab und zeigt an, dass der Thread nicht mehr fixiert ist.

4. Wechseln Sie zum Code-Editor, und drücken Sie **F11**. Es wird nur der nicht fixierte Thread ausgeführt.

    Die APP kann auch einige neue Threads instanziieren. Neue Threads werden ohne Markierung gekennzeichnet und sind nicht fixiert.

### <a name="bkmk_follow_a_thread"></a>Folgen eines einzelnen Threads mit bedingten Haltepunkten

Es kann hilfreich sein, die Ausführung eines einzelnen Threads im Debugger zu befolgen. Eine Möglichkeit hierfür ist das Einfrieren von Threads, an denen Sie nicht interessiert sind. In einigen Szenarien müssen Sie möglicherweise einen einzelnen Thread befolgen, ohne andere Threads zu fixieren, z. b. um einen bestimmten Fehler zu reproduzieren. Wenn Sie einem Thread folgen möchten, ohne andere Threads zu fixieren, müssen Sie das Unterbrechen des Codes vermeiden, mit Ausnahme des Threads, der für Sie von Interesse ist. Dies können Sie erreichen, indem Sie einen [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)festlegen.

Sie können Breakpoints für verschiedene Bedingungen festlegen, z. b. den Thread Namen oder die Thread-ID. Möglicherweise ist es hilfreich, die Bedingung für die Daten festzulegen, die für jeden Thread eindeutig sind. Dabei handelt es sich um ein gängiges Debugszenario, bei dem Sie eher an einem bestimmten Datenwert als in einem bestimmten Thread interessiert sind.

1. Klicken Sie mit der rechten Maustaste auf den zuvor erstellten Haltepunkt, und wählen Sie **Bedingungen**aus.

2. Geben Sie im Fenster "halte **Punkt Einstellungen** " `data == 5` für den bedingten Ausdruck ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Conditionalbreakpoint")

    > [!TIP]
    > Wenn Sie an einem bestimmten Thread interessiert sind, verwenden Sie einen Thread Namen oder eine Thread-ID für die Bedingung. Wählen Sie hierzu im Fenster halte **Punkt Einstellungen** die Option **Filter** anstelle von **bedingtem Ausdruck**aus, und befolgen Sie die filtertipps. Möglicherweise möchten Sie Ihre Threads in Ihrem app-Code benennen, da sich Thread-IDs ändern, wenn Sie den Debugger neu starten.

3. Schließen Sie das Fenster halte **Punkt Einstellungen** .

4. Klicken Sie auf die Schaltfläche ![App neu](../debugger/media/dbg-tour-restart.png "RestartApp") starten, um die Debugsitzung neu zu starten

    Sie unterbrechen den Code im Thread, bei dem der Wert der Daten Variablen 5 ist. Suchen Sie im Fenster **parallele Überwachung** nach dem gelben Pfeil, der den aktuellen Debugger-Kontext anzeigt.

5. Nun können Sie Code (**F10**) überspringen und in Code (**F11**) wechseln und die Ausführung des einzelnen Threads verfolgen.

    Solange die breakpointbedingung für den Thread eindeutig ist und der Debugger keine anderen Haltepunkte in anderen Threads trifft (Sie müssen Sie ggf. deaktivieren), können Sie den Code überspringen und in den Code schrittweise ausführen, ohne zu anderen Threads zu wechseln.

    > [!NOTE]
    > Wenn Sie den Debugger fortsetzen, werden alle Threads ausgeführt. Der Debugger unterbricht jedoch keinen Code in anderen Threads, es sei denn, einer der anderen Threads erreicht einen Haltepunkt.

## <a name="see-also"></a>Weitere Informationen

- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Gewusst wie: Verwenden des Fensters "parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)
- [Gewusst wie: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md)