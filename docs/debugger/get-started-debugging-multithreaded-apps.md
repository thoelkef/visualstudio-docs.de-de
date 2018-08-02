---
title: Informationen Sie zum Debuggen von Multithreadanwendungen
description: Debuggen Sie mit den Fenstern "Parallele Stapel und parallele Überwachung" in Visual Studio
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468682"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Erste Schritte zum Debuggen von Multithreadanwendungen in Visual Studio
Visual Studio bietet mehrere Tools und Elemente der Benutzeroberfläche können Sie das Debuggen von Multithreadanwendungen. In diesem Tutorial wird gezeigt, wie mit Threadmarker, der **parallele Stapel** Fenster die **parallele Überwachung** bedingter Haltepunkte, Fenster und filterhaltepunkte. Dieses Tutorial dauert nur wenige Minuten, aber vertraut, die Sie mit den Funktionen für das Debuggen von Multithreadanwendungen.

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) für Multithread-debugging, die ähnliche Schritte zeigt. |

Andere Themen enthalten weitere Informationen zur Verwendung von anderen Multithread-debugging-Tools:

- Eine ähnliche Thema, das zeigt, wie Sie mit der **Debugspeicherort** Symbolleiste und die **Threads** Fenster finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

- Für eine ähnliche Thema mit der ein Beispiel, verwendet <xref:System.Threading.Tasks.Task> (verwalteter Code) und die Concurrency Runtime (C++), finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md). Allgemeine Tipps zum Debuggen, die für die meisten Multithread-Anwendungstypen gelten, finden Sie sowohl in diesem Thema und verknüpften Thema.
  
Um zu Beginn dieses Lernprogramms benötigen Sie ein Multithreadanwendungsprojekt. Befolgen Sie die hier aufgeführten Schritte, um das Projekt zu erstellen.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>So erstellen Sie die Multithread-app-Projekt  
  
1.  Auf der **Datei** Menü wählen **neu** , und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Klicken Sie auf der Sprache Ihrer Wahl: **Visual C#-**, **Visual C++**, oder **Visual Basic**.  
  
3.  Klicken Sie unter **Windows Desktop**, wählen Sie **Konsolen-App**.  
  
4.  In der **Namen** geben den Namen MyThreadWalkthroughApp ein.  
  
5.  Klicken Sie auf **OK**.  
  
     Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der Sprache, die Sie ausgewählt haben, kann die Quelldatei Program.cs oder MyThreadWalkthroughApp.cpp "Module1.vb" aufgerufen werden.  
  
6.  Löschen Sie den Code, der in der Quelldatei angezeigt wird, und Ersetzen Sie ihn mit dem hier gezeigten Beispielcode.

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
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
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
  
7.  Auf der **Datei** Menü klicken Sie auf **Alles speichern**.  
  
#### <a name="to-begin-the-tutorial"></a>Um das Lernprogramm zu starten.  
  
-   Suchen Sie in der Quellcode-Editor nach den folgenden Code: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>So starten Sie das Debuggen  
  
1.  Klicken Sie im linken Bundsteg des der `Thread.Sleep` oder `this_thread::sleep_for` Anweisung, um einen neuen Haltepunkt einzufügen.  
  
     Im Bundsteg auf der linken Seite von der Quellcode-Editor wird ein roter Kreis. Diese Kugel zeigt an, dass an dieser Stelle jetzt ein Haltepunkt festgelegt wurde. 
  
2.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen starten** (**F5**).  
  
     Visual Studio erstellt die Projektmappe, die app gestartet wird, um mit dem angefügten Debugger auszuführen, und klicken Sie dann die app beendet die Ausführung am Haltepunkt.  
  
    > [!NOTE]
    > Wenn Sie den Fokus an das Konsolenfenster wechseln, klicken Sie in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fenster den Fokus auf zurückzugebenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Suchen Sie in der Quellcode-Editor nach der Zeile, die den Haltepunkt enthält:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Ermitteln Sie den Threadmarker  

1.  Klicken Sie in der Debug-Symbolleiste auf die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Drücken Sie **F11** einmal um den Debugger eine Codezeile zu gelangen.
  
3.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Threadmarker teilweise kann, können Sie durch einen Haltepunkt abgedeckt werden. 
  
4.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads. Der Name ist in diesem Fall wahrscheinlich `<noname>`. 
  
5.  Mit der rechten Maustaste in des Thread-Markers, um die verfügbaren Optionen im Kontextmenü anzuzeigen.
    
## <a name="ParallelStacks"></a>Zeigt den Speicherort von Threads

In der **parallele Stapel** Fenster, wechseln Sie zwischen einer Threads und (für taskbasierte Programmierung) Aufgaben anzeigen, und Sie finden Informationen in der Aufrufliste für jeden Thread. In dieser app können wir die Ansicht "Threads" verwenden.

1. Öffnen der **parallele Stapel** durch auswählen **Debuggen > Windows > Parallele Stapel**. Sie sollte etwa wie folgt (die genaue Informationen werden je nach den aktuellen Speicherort der einzelnen Threads, Ihrer Hardware und Ihre bevorzugte Programmiersprache).

    ![Fenster mit parallelen Stapeln von](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In diesem Beispiel von links nach rechts abrufen wir diese Informationen für verwalteten Code:
    
    - Der Hauptthread (linke Seite) wurde beendet, auf `Thread.Start` (die Beendigungspunkt wird angegeben, indem Sie das Symbol "Thread-Marker" ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Zwei Threads eingegeben haben die `ServerClass.InstanceMethod`, von denen der aktuelle Thread (gelben Pfeil), wird während der andere Thread, im beendet wurde `Thread.Sleep`.
    - Ein neuer Thread (rechts) wird ebenfalls gestartet (auf beendet `ThreadHelper.ThreadStart`).

2.  Mit der rechten Maustaste Einträge in der **parallele Stapel** Fenster aus, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

    Sie können verschiedene Aktionen in diese Menüs mit der rechten Maustaste, aber in diesem Tutorial erfahren Sie mehr diese Details in der **parallele Überwachung** Fenster (nächsten Abschnitten).

    > [!NOTE]
    > Wenn Sie mehr interessiert eine Liste mit Informationen für jeden Thread anzuzeigen sind, verwenden Sie die **Threads** Fenster stattdessen. Finden Sie unter [Exemplarische Vorgehensweise: Debuggen eine Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Festlegen eines Überwachungselements für eine Variable

1. Öffnen der **parallele Überwachung** durch auswählen **Debuggen > Windows > parallele Überwachung > parallele Überwachung 1**.

2. Klicken Sie auf die Zelle, sodass Sie sehen, die `<Add Watch>` Text (oder die leere Zelle in der 4. Spalte), Typ `data`, und drücken Sie EINGABETASTE.

    Die Werte für die Data-Variable für jeden Thread werden im Fenster angezeigt.

3. Klicken Sie erneut, in der Zelle, sodass Sie sehen, die `<Add Watch>` Text (oder die leere Kopfzeilenzelle in der 5. Spalte), Typ `count`, und drücken Sie EINGABETASTE.

    Die Werte für Variablen "Count" für jeden Thread werden im Fenster angezeigt. (Wenn Sie diese Menge Informationen noch nicht angezeigt wird, versuchen Sie es Drücken von F11 erneut mehrere Male, fahren Sie fort, die Ausführung der Threads im Debugger.)

    ![Fenster für parallele Stapel](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Mit der rechten Maustaste eine der Zeilen im Fenster, um die verfügbaren Optionen anzuzeigen.

## <a name="flagging-and-unflagging-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung  
Sie können Threads kennzeichnen, die besondere Aufmerksamkeit erhalten sollen. Das Kennzeichnen von Threads ist eine gute Möglichkeit zum Nachverfolgen wichtiger Threads und Threads zu ignorieren, denen Sie nicht interessiert.  
  
#### <a name="to-flag-threads"></a>So kennzeichnen Sie Threads  

1. In der **parallele Überwachung** Fenster, halten Sie die UMSCHALTTASTE gedrückt, und wählen Sie mehrere Zeilen.

2. Mit der rechten Maustaste, und wählen Sie **Flag**.

    Jetzt werden alle ausgewählten Threads gekennzeichnet. Jetzt können Sie filtern, um nur gekennzeichnete Threads angezeigt.
  
3.  In der **parallele Überwachung** Fenster Suchen der **nur gekennzeichnete Threads anzeigen** Schaltfläche ![gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Klicken Sie auf die **nur gekennzeichnete Threads anzeigen** Schaltfläche.  
  
    Jetzt wird nur der gekennzeichnete Thread in der Liste angezeigt.

    > [!TIP]
    > Wenn Sie einige Threads gekennzeichnet haben, können Sie mit der rechten Maustaste in einer einzige Zeile Code im Code-Editor und wählen Sie **gekennzeichnete Threads bis zum Cursor ausführen** (Stellen Sie sicher, dass Sie auswählen, Code, der alle gekennzeichnete Threads erreicht wird). Dies hält die Threads in der ausgewählten Zeile des Codes, erleichtert Ihnen die Steuerung die Reihenfolge der Ausführung von [sperren und Entsperren von Threads](#bkmk_freeze).

5.  Klicken Sie auf die **nur gekennzeichnete Threads anzeigen** Schaltfläche, um zurück in den wechseln **alle Threads anzeigen** Modus.
    
#### <a name="to-unflag-threads"></a>So heben Sie die Kennzeichnung von Threads auf

Um Threads Kennzeichnung aufzuheben, Sie können mit der rechten Maustaste ein oder mehrere gekennzeichnete Threads in der **parallele Überwachung** Fenster, und wählen Sie **Flag**.

## <a name="bkmk_freeze"></a> Sperren und Entsperren der Threadausführung 

> [!TIP]
> Sie können Einfrieren und reaktivieren (anhalten und fortsetzen) Threads zur Steuerung der Reihenfolge, in denen Threads Arbeiten ausführen. Damit können Sie beheben Parallelitätsprobleme wie Deadlocks und Racebedingungen.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>So sperren und entsperren Sie Threads  
  
1.  In der **parallele Überwachung** Fenster für die alle Zeilen ausgewählt haben, mit der rechten Maustaste, und wählen **fixieren**.

    In der zweiten Spalte wird eine Pausen-Symbol für jede Zeile jetzt angezeigt. Das Pausensymbol gibt an, dass der Thread gesperrt ist.

2.  Deaktivieren Sie die Zeilen durch Klicken auf die nur eine Zeile aus.

3.  Mit der rechten Maustaste einer Zeile aus, und wählen Sie **reaktivieren**.

    Das Pausensymbol verschwindet in dieser Zeile, die angibt, dass der Thread nicht mehr gesperrt ist.

4.  Wechseln Sie zum Code-Editor, und klicken Sie auf **F11**. Nur der nicht fixierte-Thread ausgeführt wird.

    Die app kann auch einige neue Threads instanziieren. Beachten Sie, dass alle neuen Threads nicht gekennzeichnet sind, und nicht fixiert werden.

## <a name="bkmk_follow_a_thread"></a> Führen Sie einen einzelnen Thread, durch das Verwenden bedingter Haltepunkte

In einigen Fällen kann es hilfreich sein, die der Ausführung von einem einzigen Thread im Debugger sein. Eine Möglichkeit, die Sie hierzu ist die Fixieren von Threads, denen Sie nicht interessiert sind, aber in einigen Szenarien möchten Sie möglicherweise führen einen einzelnen Thread ohne Sperren anderer Threads (zu reproduzieren, die eine bestimmten Fehler, z. B.). Um einen Thread auszuführen, ohne andere Threads einfrieren, müssen Sie vermeiden, unterbrechen im Code mit Ausnahme im Thread aus, die Sie interessiert sind. Sie erreichen dies durch Festlegen einer [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Sie können Haltepunkte festlegen, auf verschiedenen Bedingungen, z. B. den Threadnamen oder die Thread-ID. Eine andere Methode, die möglicherweise hilfreich ist, legen Sie die Bedingung für Daten, die Sie wissen, dass für jeden Thread eindeutig werden. Dies ist ein häufiges debugging-Szenario, in dem Sie mehr als einigen bestimmten Datenwert in einem bestimmten Thread interessiert sind.

#### <a name="to-follow-a-single-thread"></a>Folgen Sie einen einzelnen thread

1. Mit der rechten Maustaste des Haltepunkts, die Sie zuvor erstellt haben, und wählen Sie **Bedingungen**.

2. In der **Haltepunkteinstellungen** geben `data == 5` für den bedingten Ausdruck.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Wenn Sie eher an einem bestimmten Thread interessiert sind, verwenden Sie eine Threadname oder Thread-ID für die Bedingung. Zu diesem Zweck der **Haltepunkteinstellungen** wählen Sie im Fenster **Filter** anstelle von **Bedingungsausdruck**, und befolgen Sie die Filter-Tipps. Sie möchten möglicherweise nennen Sie die Threads im app-Code (da Threads IDs ändern, wenn Sie den Debugger neu starten).

3. Schließen der **Haltepunkteinstellungen** Fenster.

4. Klicken Sie auf den Neustart ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") um die Debugsitzung erneut zu starten.

    Sie werden in Code auf dem Thread unterbrechen, für die Data-Variablen 5 ist. Suchen Sie nach der gelbe Pfeil (aktueller Debuggerkontext), der **parallele Überwachung** Fenster aus, um zu überprüfen, ob.

5. Nun können Prozedurschritt (F10)-Code und Code (F11) schrittweise und führen Sie die Ausführung der einzelnen Threads.

    Solange die Bedingung für Haltepunkt für den Thread eindeutig ist und der Debugger keine anderen Haltepunkte auf anderen Threads trifft (möglicherweise müssen sie deaktiviert), können Code überspringen und Einzelschritte im Code nicht in anderen Threads wechseln.

    > [!NOTE]
    > Wenn Sie fahren fort, um den Debugger, werden alle Threads ausgeführt werden. Der Debugger wird nicht jedoch in Code in anderen Threads unterbrechen, es sei denn, eine der anderen Threads ein Haltepunkt erreicht. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Weitere Informationen zu den Multithread-debugging-Fenster 

#### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen thread 

- Um zu einem anderen Thread zu wechseln, finden Sie unter [Vorgehensweise: Wechseln Sie zu einem anderen Thread beim Debuggen](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Weitere Informationen zu den Fenstern parallele Stapel "und" Parallele Überwachung  
  
- Finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md) 

- Finden Sie unter [Vorgehensweise: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
