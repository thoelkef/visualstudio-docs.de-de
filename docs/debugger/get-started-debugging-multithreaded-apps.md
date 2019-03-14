---
title: Informationen Sie zum Debuggen von Multithreadanwendungen
description: Debuggen Sie mit den Fenstern "Parallele Stapel und parallele Überwachung" in Visual Studio
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
ms.openlocfilehash: 671af69cf31ad1b8b5adafa413e4f20a8761d5ce
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526037"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Erste Schritte zum Debuggen von Multithreadanwendungen (C#, Visual Basic, C++)

Visual Studio bietet mehrere Tools und Elemente der Benutzeroberfläche können Sie das Debuggen von Multithreadanwendungen. In diesem Tutorial wird gezeigt, wie mit Threadmarker, der **parallele Stapel** Fenster die **parallele Überwachung** bedingter Haltepunkte, Fenster und filterhaltepunkte. Das Abschließen dieses Lernprogramms werden Sie mit Visual Studio-Funktionen für das Debuggen von Multithreadanwendungen vertraut machen.

Diese zwei Themen enthalten weitere Informationen zur Verwendung von anderen Multithread-debugging-Tools:

- Verwenden der **Debugspeicherort** Symbolleiste und die **Threads** Fenster finden Sie unter [Exemplarische Vorgehensweise: Debuggen eine Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

- Ein Beispiel, verwendet <xref:System.Threading.Tasks.Task> (verwalteter Code) und die Concurrency Runtime (C++), finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md). Finden Sie allgemeine Tipps zum Debuggen, die für die meisten Multithread-Anwendungstypen gelten sowohl für dieses Thema als auch für diese.

Zunächst benötigen Sie ein Multithreadanwendungsprojekt. Im Folgenden wird ein Beispiel aufgeführt.

## <a name="create-a-multithreaded-app-project"></a>Erstellen Sie ein Multithread-app-Projekt

1.  Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2.  Wählen Sie eine Sprache: **Visual C#** , **Visual C++**, oder **Visual Basic**.

3.  Klicken Sie unter **Windows Desktop**, wählen Sie **Konsolen-App**.

4.  In der **Namen** geben MyThreadWalkthroughApp ein.

5.  Klicken Sie auf **OK**.

     Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der Sprache, die Sie ausgewählt haben, kann die Quelldatei aufgerufen werden *"Program.cs"*, *MyThreadWalkthroughApp.cpp*, oder *"Module1.vb"*.

6.  Löschen Sie den Code, der in der Quelldatei angezeigt wird, und Ersetzen Sie sie mit der entsprechenden Beispiel codeauflistung unten.

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
                "The instance method called by the worker thread has ended.");
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
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
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
                    "The instance method called by the worker thread has ended.")
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

7.  Wählen Sie im Menü **Datei** den Befehl **Alle speichern** aus.

8. (Nur Visual Basic) Maustaste Sie im Projektmappen-Explorer (rechter Bereich) auf den Projektknoten, wählen **Eigenschaften**. Unter den **Anwendung** Registerkarte die **Startobjekt** zu **einfache**.

## <a name="debug-the-multithreaded-app"></a>Debuggen Sie die Multithread-app

1. Suchen Sie in der Quellcode-Editor nach einer der folgenden Codeausschnitte:

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

1. Klicken Sie im linken Bundsteg des der `Thread.Sleep` oder `std::this_thread::sleep_for` Anweisung, um einen neuen Haltepunkt einzufügen.

    Im Bundsteg gibt ein roter Kreis an, dass ein Haltepunkt an dieser Stelle festgelegt wurde.

2. Auf der **Debuggen** , wählen Sie im Menü **Debuggen starten** (**F5**).

    Visual Studio erstellt die Projektmappe, die app gestartet wird, um mit dem angefügten Debugger auszuführen, und klicken Sie dann die app beendet die Ausführung am Haltepunkt.

3. Suchen Sie in der Quellcode-Editor die Zeile, die den Haltepunkt enthält.

### <a name="ShowThreadsInSource"></a>Ermitteln Sie den Threadmarker  

1.  Wählen Sie in der Debug-Symbolleiste die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Drücken Sie **F11** einmal um den Debugger eine Codezeile zu gelangen.

3.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , die zwei twisted Threads ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Ein Threadmarker kann teilweise durch einen Haltepunkt verborgen werden.

4.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt, dass Sie die Namen und die Thread-ID jedes angehaltenen Threads. Der Name ist in diesem Fall wahrscheinlich `<noname>`.

5.  Wählen Sie den Threadmarker, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

### <a name="ParallelStacks"></a>Anzeigen der Thread-Orte

In der **parallele Stapel** Fenster, wechseln Sie zwischen einer Threads und (für taskbasierte Programmierung) Aufgaben anzeigen, und Sie finden Informationen in der Aufrufliste für jeden Thread. In dieser app können wir die Ansicht "Threads" verwenden.

1. Öffnen der **parallele Stapel** durch auswählen **Debuggen** > **Windows** > **parallele Stapel**. Sie sollte in etwa Folgendes angezeigt werden. Die genaue Informationen variieren je nach den aktuellen Speicherort der einzelnen Threads, Ihrer Hardware und Ihre bevorzugte Programmiersprache.

    ![Fenster mit parallelen Stapeln von](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In diesem Beispiel sehen Sie von links nach rechts diese Informationen für verwalteten Code:

    - Der Hauptthread (linke Seite) wurde beendet, auf `Thread.Start`, in denen die Beendigungspunkt angegeben wird, durch das Symbol "Thread-Marker" ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Zwei Threads eingegeben haben die `ServerClass.InstanceMethod`, von denen der aktuelle Thread (gelben Pfeil), wird während der andere Thread, im beendet wurde `Thread.Sleep`.
    - Ein neuer Thread (rechts) wird auch gestartet, aber auf beendet ist `ThreadHelper.ThreadStart`.

2.  Mit der rechten Maustaste Einträge in der **parallele Stapel** Fenster aus, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

    Sie können verschiedene Aktionen in diese Menüs mit der rechten Maustaste, aber in diesem Tutorial erfahren Sie mehr diese Details in der **parallele Überwachung** Fenster (nächsten Abschnitten).

    > [!NOTE]
    > Um eine Liste mit Informationen für jeden Thread anzeigen zu anzuzeigen, verwenden die **Threads** Fenster stattdessen. Finden Sie unter [Exemplarische Vorgehensweise: Debuggen eine Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Festlegen eines überwachungselements für eine variable

1. Öffnen der **parallele Überwachung** Fenster durch Auswahl **Debuggen** > **Windows** > **parallele Überwachung**  >  **Parallele Überwachung 1**.

2. Wählen Sie die Zelle, sodass Sie sehen, die `<Add Watch>` Text (oder die leere Zelle in der 4. Spalte), und geben Sie `data`.

    Die Werte für die Data-Variable für jeden Thread werden im Fenster angezeigt.

3. Wählen Sie die Zelle, sodass Sie sehen, die `<Add Watch>` Text (oder die leere Kopfzeilenzelle in der 5. Spalte), und geben Sie `count`.

    Die Werte für die `count` Variable für jeden Thread im Fenster angezeigt. Wenn Sie diese Menge Informationen noch nicht angezeigt wird, versuchen Sie es drücken **F11** wenige Male, um die Ausführung der Threads im Debugger zu gelangen.

    ![Fenster für parallele Stapel](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Mit der rechten Maustaste auf eine der Zeilen im Fenster, um die verfügbaren Optionen anzuzeigen.

### <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung
Sie können Threads zum Nachverfolgen wichtiger Threads und ignoriert die anderen Threads kennzeichnen.

1. In der **parallele Überwachung** Fenster, halten Sie die **UMSCHALT** gedrückt, und wählen Sie mehrere Zeilen.

2. Mit der rechten Maustaste, und wählen Sie **Flag**.

    Alle ausgewählten Threads werden gekennzeichnet. Jetzt können Sie filtern, um nur gekennzeichnete Threads angezeigt.

3.  In der **parallele Überwachung** wählen Sie im Fenster der **nur gekennzeichnete Threads anzeigen** Schaltfläche ![gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Nur die gekennzeichneten Threads, die in der Liste angezeigt werden.

    > [!TIP]
    > Nachdem Sie einige Threads gekennzeichnet haben, können Sie mit der rechten Maustaste in einer einzige Zeile Code im Code-Editor und wählen Sie **gekennzeichnete Threads bis zum Cursor ausführen**. Stellen Sie sicher, um auszuwählen, dass Code, der alle gekennzeichnete Threads erreicht wird. Visual Studio hält Threads in der ausgewählten Zeile des Codes, erleichtert Ihnen die Steuerung die Reihenfolge der Ausführung von [sperren und Entsperren von Threads](#bkmk_freeze).

4.  Wählen Sie die **nur gekennzeichnete Threads anzeigen** Schaltfläche erneut aus, um zurück in den wechseln **alle Threads anzeigen** Modus.

5. Zum Aufheben der Kennzeichnung von Threads Maustaste einen oder mehrere gekennzeichnete Threads in der **parallele Überwachung** Fenster, und wählen **Flag**.

### <a name="bkmk_freeze"></a> Einfrieren Sie und reaktivieren Sie die Ausführung des Threads

> [!TIP]
> Sie können Einfrieren und reaktivieren (anhalten und fortsetzen) Threads zur Steuerung der Reihenfolge, in denen Threads Arbeiten ausführen. Damit können Sie beheben Parallelitätsprobleme wie Deadlocks und Racebedingungen.

1.  In der **parallele Überwachung** Fenster für die alle Zeilen ausgewählt haben, mit der rechten Maustaste, und wählen **fixieren**.

    In der zweiten Spalte wird Sie für jede Zeile eine Pausen-Symbol angezeigt. Das Pausensymbol gibt an, dass der Thread gesperrt ist.

2.  Deaktivieren Sie alle anderen Zeilen dazu nur eine Zeile aus.

3.  Mit der rechten Maustaste einer Zeile aus, und wählen Sie **reaktivieren**.

    Das Pausensymbol verschwindet in dieser Zeile, die angibt, dass der Thread nicht mehr gesperrt ist.

4.  Wechseln Sie zu dem Code-Editor, und drücken Sie **F11**. Nur der nicht fixierte-Thread ausgeführt wird.

    Die app kann auch einige neue Threads instanziieren. Alle neuen Threads sind nicht gekennzeichnet und nicht fixiert werden.

### <a name="bkmk_follow_a_thread"></a> Führen Sie einen einzelnen Thread mit bedingter Haltepunkte

Es kann hilfreich sein, die der Ausführung von einem einzigen Thread im Debugger sein. Eine Möglichkeit dazu besteht das Fixieren von Threads, denen Sie nicht interessiert sind. In einigen Szenarien müssen Sie einen einzelnen Thread zu folgen, ohne zu fixieren von anderen Threads, z. B. um einen bestimmten Fehler zu reproduzieren. Um einen Thread auszuführen, ohne andere Threads einfrieren, müssen Sie vermeiden, unterbrechen im Code mit Ausnahme im Thread aus, die Sie interessiert sind. Sie erreichen dies durch Festlegen einer [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Sie können Haltepunkte festlegen, auf verschiedenen Bedingungen, z. B. den Threadnamen oder die Thread-ID. Es ist möglicherweise hilfreich sind, um die Bedingung für Daten festlegen, die Sie wissen, für jeden Thread eindeutig ist. Dies ist ein häufiges debugging-Szenario, in dem Sie mehr als einigen bestimmten Datenwert in einem bestimmten Thread interessiert sind.

1. Mit der rechten Maustaste des Haltepunkts, die Sie zuvor erstellt haben, und wählen Sie **Bedingungen**.

2. In der **Haltepunkteinstellungen** Fenster eingeben `data == 5` für den bedingten Ausdruck.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Wenn Sie eher an einem bestimmten Thread interessiert sind, verwenden Sie eine Threadname oder Thread-ID für die Bedingung. Zu diesem Zweck der **Haltepunkteinstellungen** wählen Sie im Fenster **Filter** anstelle von **Bedingungsausdruck**, und befolgen Sie die Filter-Tipps. Sie können Ihre Threads in Ihrem app-Code benennen möchten wie Threads IDs ändern, wenn Sie den Debugger neu starten.

3. Schließen der **Haltepunkteinstellungen** Fenster.

4. Wählen Sie den Neustart ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") um die Debugsitzung erneut zu starten.

    Sie werden in den Code für den Thread unterbrechen, in denen den Wert der Datenvariablen 5 ist. In der **parallele Überwachung** suchen Sie nach der gelbe Pfeil, der angibt, des aktuelle Kontexts für die Debugger-Fenster.

5. Sie können jetzt über den Code schrittweise (**F10**) und Code schrittweise (**F11**), und befolgen Sie die Ausführung der einzelnen Threads.

    Solange die Bedingung für Haltepunkt für den Thread eindeutig ist und der Debugger keine anderen Haltepunkte auf anderen Threads trifft (möglicherweise müssen sie deaktiviert), können Sie Code überspringen und Einzelschritte im Code nicht in anderen Threads wechseln.

    > [!NOTE]
    > Wenn Sie fahren fort, um den Debugger, werden alle Threads ausgeführt werden. Der Debugger wird nicht jedoch in Code in anderen Threads unterbrechen, es sei denn, eine der anderen Threads ein Haltepunkt erreicht.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Gewusst wie: Verwenden Sie das Fenster "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)
- [Gewusst wie: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md)