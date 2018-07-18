---
title: Weitere Informationen Sie zum Debuggen von Multithreadanwendungen
description: Debuggen Sie mit der parallele Stapel und parallele Überwachung Fenstern in Visual Studio
ms.custom: H1HackMay2017
ms.date: 06/02/2017
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
ms.openlocfilehash: bb178a0a048a3696fc2c1ec642127906c8b83424
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926259"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Erste Schritte zum Debuggen von Multithreadanwendungen in Visual Studio
Visual Studio bietet mehrere Tools und Elemente der Benutzeroberfläche können Sie das Debuggen von Multithreadanwendungen. Dieses Lernprogramm zeigt, wie Threadmarker, die **parallele Stapel** Fenster die **parallele Überwachung** für Fenster, bedingte Haltepunkte und Filter Haltepunkte. In diesem Lernprogramm dauert nur wenige Minuten, aber vertraut, die Sie mit den Funktionen für das Debuggen von Multithreadanwendungen verwendet werden können.

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [In diesem Video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) für Multithread-debugging, die ähnliche Schritte veranschaulicht. |

Weitere Themen enthalten zusätzliche Informationen zur Verwendung von anderen Multithread Tools zum Debuggen:

- Für eine ähnliche Thema, das zeigt, wie Sie die **Debugspeicherort** Symbolleiste und die **Threads** Fenster finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

- Für eine ähnliche Thema mit einem Beispiel, verwendet <xref:System.Threading.Tasks.Task> (verwalteter Code) und die Concurrency Runtime (C++), finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md). Allgemeine Tipps zum Debuggen, die für die meisten Multithread Anwendungstypen gelten, finden Sie in diesem Thema und den verknüpften Themen.
  
Um dieses Lernprogramm beginnen, benötigen Sie ein Multithreadanwendungsprojekt. Befolgen Sie die hier aufgeführten Schritte, um das Projekt zu erstellen.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>So erstellen Sie die Multithread-app-Projekt  
  
1.  Auf der **Datei** Menü wählen **neu** , und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Projekttyp**s Klicken Sie auf der Sprache Ihrer Wahl: **Visual C#-**, **Visual C++**, oder **Visual Basic**.  
  
3.  In der **Vorlagen** wählen **Konsolen-App**.  
  
4.  In der **Namen** Feld Geben Sie den Namen MyThreadWalkthroughApp ein.  
  
5.  Klicken Sie auf **OK**.  
  
     Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der Sprache, die Sie ausgewählt haben, kann die Quelldatei "Program.cs", MyThreadWalkthroughApp.cpp oder "Module1.vb" aufgerufen werden.  
  
6.  Löschen Sie den Code, der in der Quelldatei angezeigt wird, und Ersetzen Sie ihn durch den Beispielcode, der hier gezeigten.

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
  
7.  Auf der **Datei** Menü klicken Sie auf **alle speichern**.  
  
#### <a name="to-begin-the-tutorial"></a>Um das Lernprogramm zu starten  
  
-   Suchen Sie in der Quellcode-Editor nach den folgenden Code: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>So starten Sie das Debuggen  
  
1.  Klicken Sie im linken Bundsteg des auf der `Thread.Sleep` oder `Thread::Sleep` Anweisung zum Einfügen eines neuen Haltepunkts.  
  
     Im Bundsteg auf der linken Seite des Quellcode-Editors wird ein roter Kreis. Diese Kugel zeigt an, dass an dieser Stelle jetzt ein Haltepunkt festgelegt wurde. 
  
2.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen** (**F5**).  
  
     Visual Studio erstellt die Lösung, die app gestartet wird, um mit dem angefügten Debugger auszuführen und dann die Anwendung am Haltepunkt beendet wird.  
  
    > [!NOTE]
    > Wenn Sie den Fokus an das Konsolenfenster zu ändern, klicken Sie in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fenster den Fokus auf den zurückzugebenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Suchen Sie in der Quellcode-Editor nach der Zeile, die den Breakpoint enthält:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Ermitteln Sie den Threadmarker  

1.  Klicken Sie in der Debug-Symbolleiste auf die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Drücken Sie **F11** einmal auf, die Debugger eine Codezeile wechseln.
  
3.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Threadmarker teilweise durch einen Haltepunkt ausgeblendet werden kann. 
  
4.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads. Der Name ist in diesem Fall wahrscheinlich `<noname>`. 
  
5.  Mit der rechten Maustaste in des Thread-Markers, um die verfügbaren Optionen im Kontextmenü anzuzeigen.
    
## <a name="ParallelStacks"></a>Zeigt den Speicherort von Threads

In der **parallele Stapel** Fenster, wechseln Sie zwischen einem Threadansicht und (für aufgabenbasierte-Programmierung) Aufgabenansicht, und Sie können anzeigen Aufruflisteninformationen für jeden Thread. In dieser app können wir die Threadansicht.

1. Öffnen der **parallele Stapel** durch auswählen **Debuggen > Windows > Parallele Stapel**. Sie sollte etwa wie folgt angezeigt (die exakte Angaben wird abhängig von der aktuellen Position von jeder Thread, der Hardware und Ihre Programmiersprache unterschiedlich sein).

    ![Fenster mit parallelen Stapeln von](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In diesem Beispiel wird von links nach rechts abrufen wir diese Informationen:
    
    - Der Hauptthread (linke Seite) wurde beendet, auf `Thread.Start` (durch das Symbol "Thread-Marker" gibt den Beenden an ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Zwei Threads eingegeben haben die `ServerClass.InstanceMethod`, von denen des aktuellen Threads (gelben Pfeil), wird während der andere Thread, im beendet wurde `Thread.Sleep`.
    - Ein neuer Thread (auf der rechten Seite) ebenfalls gestartet wird (auf dem `ThreadHelper.ThreadStart`).

2.  Mit der rechten Maustaste Einträge in der **parallele Stapel** Fenster aus, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

    Sie können verschiedene Aktionen aus diesen Kontextmenüs, aber für dieses Lernprogramm erfahren wir, weitere Teil dieser detaillierten Informationen in den **parallele Überwachung** Fenster (nächsten Abschnitten).

    > [!NOTE]
    > Wenn Sie mehr interessiert, sehen eine Liste mit Informationen für jeden Thread anzuzeigen, verwenden Sie die **Threads** Fenster stattdessen. Finden Sie unter [Exemplarische Vorgehensweise: Debuggen eine Multithreadanwendung](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Legen Sie eine Überwachung auf eine Variable

1. Öffnen der **parallele Überwachung** durch auswählen **Debuggen > Windows > parallele Überwachung > parallele Überwachung 1**.

2. Klicken Sie auf die Zelle, in dem Sie sehen, die `<Add Watch>` Text (oder die leere Zelle 4. Spalte) Typ `data`, und drücken Sie die EINGABETASTE.

    Im Fenster werden die Werte für die Datenvariable für jeden Thread angezeigt.

3. Klicken Sie erneut auf die Zelle, in dem Sie sehen, die `<Add Watch>` Text (oder die leere Kopfzeilenzelle in der Spalte 5.) Typ `count`, und drücken Sie die EINGABETASTE.

    Im Fenster werden die Werte für die Count-Variable für jeden Thread angezeigt. (Wenn noch viel Informationen nicht angezeigt wird, versuchen Sie, drücken F11 erneut mehrere Male, um die Ausführung der Threads im Debugger zu wechseln.)

    ![Fenster für parallele Stapel](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Klicken Sie auf eine der Zeilen in einem Fenster auf die verfügbaren Optionen anzuzeigen.

## <a name="flagging-and-unflagging-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung  
Sie können Threads kennzeichnen, die besondere Aufmerksamkeit erhalten soll. Das Kennzeichnen von Threads ist eine gute Möglichkeit zum Nachverfolgen wichtiger Threads und Threads zu ignorieren, denen Sie uninteressant ist.  
  
#### <a name="to-flag-threads"></a>So kennzeichnen Sie Threads  

1. In der **parallele Überwachung** Fenster, die UMSCHALT-Taste gedrückt halten und mehrere Zeilen auswählen.

2. Mit der rechten Maustaste, und wählen Sie **Flag**.

    Nun werden alle ausgewählten Threads gekennzeichnet. Jetzt können Sie filtern, um nur gekennzeichnete Threads anzeigen.
  
3.  In der **parallele Überwachung** Fenster Suchen der **nur gekennzeichnete Threads anzeigen** Schaltfläche ![gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Klicken Sie auf die **nur gekennzeichnete Threads anzeigen** Schaltfläche.  
  
    Jetzt wird nur der gekennzeichnete Thread in der Liste angezeigt.

    > [!TIP]
    > Wenn Sie einige Threads markiert haben, können Sie mit der rechten Maustaste einer Codezeile im Code-Editor und wählen Sie **gekennzeichnete Threads Ausführen bis Cursor** (Stellen Sie sicher, dass Sie Code, der alle gekennzeichnete Threads gelangen auswählen). Dies wird in der ausgewählten Zeile des Codes, die einfacher zu steuern, die Reihenfolge der Ausführung von Threads anhalten [sperren und Entsperren von Threads](#bkmk_freeze).

5.  Klicken Sie auf die **nur gekennzeichnete Threads anzeigen** Schaltfläche, um zurück in den wechseln **alle Threads anzeigen** Modus.
    
#### <a name="to-unflag-threads"></a>So heben Sie die Kennzeichnung von Threads auf

Zum Aufheben der Kennzeichnung von Threads können Rechtsklick auf eine oder mehrere gekennzeichnete Threads in der **parallele Überwachung** Fenster, und wählen Sie **Flag**.

## <a name="bkmk_freeze"></a> Sperren und Entsperren der Threadausführung 

> [!TIP]
> Sie können Einfrieren und reaktivieren (anhalten und fortsetzen) Threads zur Steuerung der Reihenfolge, in denen Threads Arbeit ausführen. Dadurch können Sie Parallelitätsprobleme wie Deadlocks und Racebedingungen.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>So sperren und entsperren Sie Threads  
  
1.  In der **parallele Überwachung** angezeigt, wobei alle Zeilen ausgewählt, mit der rechten Maustaste und wählen Sie **fixieren**.

    Ein Symbol "Anhalten" in der zweiten Spalte für jede Zeile jetzt angezeigt. Das Pausensymbol gibt an, dass der Thread gesperrt ist.

2.  Deaktivieren Sie die Zeilen durch Klicken auf eine Zeile nur ein.

3.  Mit der rechten Maustaste einer Zeile, und wählen Sie **reaktivieren**.

    Das Pausensymbol verschwindet in dieser Zeile, gibt an, dass der Thread nicht mehr gesperrt ist.

4.  Wechseln Sie zu dem Code-Editor, und klicken Sie auf **F11**. Nur der nicht fixierte Thread ausgeführt wird.

    Die app kann auch einige neue Threads instanziiert werden. Beachten Sie, dass keine neuen Threads nicht gekennzeichnet sind und sind nicht fixiert.

## <a name="bkmk_follow_a_thread"></a> Führen Sie einen einzelnen Thread mit bedingter Haltepunkte

In einigen Fällen können sie die Ausführung von einem einzelnen Thread im Debugger hilfreich sein. Eine Möglichkeit, die Sie dafür ist das Fixieren von Threads, denen Sie nicht interessiert sind, aber in einigen Szenarien möchten Sie möglicherweise führen einen einzelnen Thread ohne das Fixieren von anderen Threads (zu reproduzieren, die eine bestimmten Fehler, z. B.). Um einen Thread ohne andere Threads Einfrieren folgen zu können, müssen Sie vermeiden, unterbrechen im Code außer auf dem Thread, dem Sie interessiert sind. Hierzu können Sie durch Festlegen einer [bedingter Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Sie können Haltepunkte festlegen, auf unterschiedliche Bedingungen, z. B. den Threadnamen oder die Thread-ID. Eine andere Methode, die möglicherweise hilfreich ist, die Bedingung auf Daten, die Sie wissen, für jeden Thread eindeutig ist. Dies ist eine allgemeine Debugszenarios, in denen Sie mehr als einigen bestimmten Datenwert in einem bestimmten Thread interessiert sind.

#### <a name="to-follow-a-single-thread"></a>Befolgen Sie einen einzelnen thread

1. Mit der rechten Maustaste des Haltepunkts, die Sie zuvor erstellt haben, und wählen Sie **Bedingungen**.

2. In der **Haltepunkteinstellungen** geben `data == 5` für den bedingten Ausdruck.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Wenn Sie einen bestimmten Thread mehr interessiert sind, verwenden Sie dann einen Threadnamen oder die Thread-ID für die Bedingung. Zu diesem Zweck in der **Haltepunkteinstellungen** wählen **Filter** anstelle von **Bedingungsausdruck**, und befolgen Sie die Filter. Möglicherweise möchten Benennen von Threads im app-Code (da Threads IDs ändern, wenn Sie den Debugger starten).

3. Schließen der **Haltepunkteinstellungen** Fenster.

4. Klicken Sie auf den Neustart ![App starten](../debugger/media/dbg-tour-restart.png "RestartApp") Schaltfläche, um die Debugsitzung neu zu starten.

    Sie werden in Code für den Thread unterbrechen, für die die Datenvariable 5 ist. Suchen Sie nach der gelbe Pfeil (aktuelle Debuggerkontext) in der **parallele Überwachung** Fenster aus, um zu überprüfen, ob.

5. Sie können jetzt überspringen von Code (F10) und Einzelschritte im Code (F11) und führen Sie die Ausführung der einzelnen Threads.

    Solange die Bedingung für Haltepunkt an den Thread eindeutig ist, und der Debugger keine anderen Breakpoints für andere Threads (möglicherweise müssen diese deaktivieren) erreicht, können über den Code schrittweise und Einzelschritte im Code ohne den für andere Threads.

    > [!NOTE]
    > Wenn Sie den Debugger zu gelangen, werden alle Threads ausgeführt. Allerdings wird nicht unterbricht der Debugger Code für andere Threads, wenn eine der anderen Threads einen Haltepunkt trifft. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Weitere Informationen zu den Multithread-debugging-Fenster 

#### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen thread 

- Um zu einem anderen Thread zu wechseln, finden Sie unter [wie: Wechseln Sie zu einem anderen Thread beim Debuggen](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Weitere Informationen zu den Fenstern parallele Stapel und parallele Überwachung  
  
- Finden Sie unter [Vorgehensweise: Verwenden des Fensters Parallele Stapel](../debugger/using-the-parallel-stacks-window.md) 

- Finden Sie unter [Vorgehensweise: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
