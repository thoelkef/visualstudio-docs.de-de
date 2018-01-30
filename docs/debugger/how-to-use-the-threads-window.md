---
title: Debuggen eine Multithreadanwendung mithilfe des Fensters Threads | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 367bade1041012670ae47937c21be42e38157dca
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung in Visual Studio mithilfe des Fensters Threads
Visual Studio bietet eine **Threads** und anderen Elementen können Sie das Debuggen von Multithreadanwendungen der Benutzeroberfläche. Dieses Lernprogramm zeigt, wie die **Threads** Fenster und die **Debugspeicherort** Symbolleiste. Weitere Informationen zu anderen Tools, finden Sie unter [erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md). In diesem Lernprogramm dauert nur wenige Minuten, aber vertraut, die Sie mit den Funktionen für das Debuggen von Multithreadanwendungen verwendet werden können.   
  
Um dieses Lernprogramm beginnen, benötigen Sie ein Multithreadanwendungsprojekt. Befolgen Sie die hier aufgeführten Schritte, um das Projekt zu erstellen.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>So erstellen Sie die Multithread-app-Projekt  
  
1.  Auf der **Datei** Menü wählen **neu** , und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Projekttyp**s Klicken Sie auf der Sprache Ihrer Wahl: **Visual Basic**, **Visual C#-**, oder **Visual C++**.  
  
3.  In der **Vorlagen** wählen **Konsolen-App**.  
  
4.  In der **Namen** Feld Geben Sie den Namen MyThreadWalkthroughApp ein.  
  
5.  Klicken Sie auf **OK**.  
  
     Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der ausgewählten Programmiersprache hat die Quelldatei die Bezeichnung Module1.vb, Program.cs oder MyThreadWalkthroughApp.cpp.  
  
6.  Löschen Sie den Code, der in der Quelldatei angezeigt wird, und Ersetzen Sie ihn durch den Beispielcode, der im Abschnitt "Erstellen eines Threads" des Themas [Threads erstellen und übergeben von Daten zur Startzeit](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Auf der **Datei** Menü klicken Sie auf **alle speichern**.  
  
#### <a name="to-begin-the-tutorial"></a>Um das Lernprogramm zu starten  
  
-   Suchen Sie in der Quellcode-Editor nach den folgenden Code:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>So starten Sie das Debuggen  
  
1.  Klicken Sie im linken Bundsteg des auf der `Console.WriteLine` Anweisung zum Einfügen eines neuen Haltepunkts.  
  
     Im Bundsteg auf der linken Seite des Quellcode-Editors wird ein roter Kreis. Diese Kugel zeigt an, dass an dieser Stelle jetzt ein Haltepunkt festgelegt wurde.  
  
2.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen** (**F5**).  
  
     Der Debugvorgang beginnt, die Konsolenanwendung wird gestartet und hält dann am Haltepunkt an.  
  
3.  Wenn sich der Fokus zu diesem Zeitpunkt im Fenster der Konsolenanwendung befindet, klicken Sie in das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Fenster, um den Fokus wieder an [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zurückzugeben.  
  
4.  Suchen Sie in der Quellcode-Editor nach der Zeile mit den folgenden Code:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>So ermitteln Sie den Threadmarker  

1.  Klicken Sie in der Debug-Symbolleiste auf die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.  
  
3.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads. In diesem Fall gibt es nur einen Thread, dessen Name wahrscheinlich `<noname>` lautet.  

    > [!TIP]
    > Sie können es namenlos Threads zu identifizieren, indem Sie diese umbenennen hilfreich sein. Wählen Sie im Fenster Threads **umbenennen** nach mit der rechten Maustaste auf die **Namen** Spalte in der Zeile Thread.
  
4.  Mit der rechten Maustaste in des Thread-Markers, um die verfügbaren Optionen im Kontextmenü anzuzeigen. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung  
Sie können Threads kennzeichnen, die besondere Aufmerksamkeit erhalten soll. Das Kennzeichnen von Threads ist eine gute Möglichkeit zum Nachverfolgen wichtiger Threads und Threads zu ignorieren, denen Sie uninteressant ist.  
  
#### <a name="to-flag-threads"></a>So kennzeichnen Sie Threads   

1.  Auf **Ansicht** Sie im Menü **Symbolleisten**.  
  
    Stellen Sie sicher, dass die **Debugspeicherort** Symbolleiste ausgewählt ist.

2.  Wechseln Sie zu der **Debugspeicherort** Symbolleiste, und klicken Sie auf die **Thread** Liste.  
  
    > [!NOTE]
    >  Diese Symbolleiste erkennen Sie an den drei gut sichtbaren Listen: **Prozess**, **Thread**, und **Stapelrahmen**.  
  
3.  Beachten Sie, wie viele Threads in der Liste angezeigt werden.  
  
4.  Wechseln Sie zurück zu den Quellcode-Editor der rechten Maustaste auf den Threadmarker ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") erneut aus.  
  
5.  Zeigen Sie im Kontextmenü auf **Flag**, und klicken Sie dann auf den Threadnamen und die ID-Nummer.  
  
6.  Wechseln Sie zurück zum **Debugspeicherort** Symbolleiste, und suchen die **nur gekennzeichnete Threads anzeigen** Symbol ![gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") auf die rechts von der **Thread** Liste.  
  
    Das Symbol "Flags" auf die Schaltfläche war zuvor abgeblendet. Jetzt hat sie eine aktive Schaltfläche.  
  
7.  Klicken Sie auf die **nur gekennzeichnete Threads anzeigen** Symbol.  
  
    Jetzt wird nur der gekennzeichnete Thread in der Liste angezeigt. (Sie können die einzelnen Kennzeichnungsschaltfläche, um zurück in den wechseln klicken **alle Threads anzeigen** Modus.)

8. Öffnen des Fensters Threads durch Auswahl **Debuggen > Windows > Threads**.

    ![Im Fenster Threads](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    In der **Threads** Fenster, der gekennzeichnete Thread hat eine rote Kennzeichnungssymbol darauf.

    > [!TIP]
    > Wenn Sie einige Threads markiert haben, können Sie mit der rechten Maustaste einer Codezeile im Code-Editor und wählen Sie **gekennzeichnete Threads Ausführen bis Cursor** (Stellen Sie sicher, dass Sie Code, der alle gekennzeichnete Threads gelangen auswählen). Dies wird in der ausgewählten Zeile des Codes, wodurch es einfacher steuern, die Reihenfolge der Ausführung von Threads anhalten [sperren und Entsperren von Threads](#bkmk_freeze).
  
11. Der Quellcode-Editor mit der Maustaste des Threadmarker erneut aus.  
  
     Beachten Sie, welche Auswahlen jetzt im Kontextmenü verfügbar sind. Anstelle von **Flag**, sehen Sie jetzt **Flag**. Klicken Sie nicht auf **Flag**.  

     Um herauszufinden, wie Sie die Kennzeichnung von Threads, fahren Sie mit dem nächsten Verfahren fort.  
  
#### <a name="to-unflag-threads"></a>So heben Sie die Kennzeichnung von Threads auf  
  
1.  In der **Threads** Fenster mit der rechten Maustaste in der Zeile, die dem gekennzeichneten Thread entspricht.  
  
     Ein Kontextmenü wird angezeigt. Es bietet Optionen zum **Flag** und **Kennzeichnung aller Threads**.  
  
2.  Klicken Sie zum Aufheben der Kennzeichnung von Threads auf **Flag**.  

    Betrachten Sie die **Debugspeicherort** Symbolleiste erneut. Die **nur gekennzeichnete Threads anzeigen** Schaltfläche ist wieder abgeblendet. Sie haben die Kennzeichnung des einzigen gekennzeichneten Threads aufgehoben. Da keine gekennzeichneten Threads vorhanden sind, die Symbolleiste auf wieder verlassen hat **alle Threads anzeigen** Modus. Klicken Sie auf die **Thread** aus, und stellen Sie sicher, dass Sie alle Threads angezeigt werden.  
  
5.  Wechseln Sie zurück zu den **Threads** Fenster, und untersuchen Sie die Informationsspalten.  
  
    Beachten Sie in der ersten Spalte ein Gliederung Flaggensymbol in jeder Zeile der Threadliste. (Die Gliederung bedeutet, dass der Thread nicht gekennzeichnet ist.)  
  
6.  Klicken Sie auf das Flag Gliederung Symbole für zwei Threads, die zweite und dritte vom unteren Ende der Liste. 

    Die Kennzeichensymbole werden in der Volltonfarbe Rot und nicht als leere Umrisslinien dargestellt.  
  
7.  Klicken Sie auf die Schaltfläche oben in der Kennzeichenspalte.  
  
    Die Reihenfolge der Threadliste wurde geändert, als Sie auf die Schaltfläche geklickt haben. Die Threadliste ist jetzt neu sortiert, und die gekennzeichneten Threads befinden sich am Anfang.  
  
8.  Klicken Sie erneut auf die Schaltfläche am Anfang der Kennzeichenspalte.  
  
    Die Sortierreihenfolge wurde wieder geändert.  
  
## <a name="more-about-the-threads-window"></a>Weitere Informationen zum Threadfenster  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Weitere Informationen zum Threadfenster  
  
1.  In der **Threads** Fenster, überprüfen Sie die dritte Spalte von links. Die Schaltfläche am Anfang dieser Spalte **ID**.  
  
2.  Klicken Sie auf **ID**.  
  
     Die Threadliste wird jetzt nach Thread-ID sortiert.  
  
3.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Thread in der Liste. Klicken Sie im Kontextmenü auf **Hexadezimale Anzeige**.  
  
     Das Format der Thread-IDs wird geändert.  
  
4.  Zeigen Sie den Mauszeiger auf die **Speicherort** Spalte für einen beliebigen Thread in der Liste.  
  
     Nach einer kurzen Verzögerung wird ein DataTip eingeblendet. Er enthält eine teilweise Aufrufliste für den Thread.

     > [!TIP]
     > Öffnen Sie eine grafische Ansicht der Aufruflisten von Threads, die [parallele Stapel](../debugger/using-the-parallel-stacks-window.md) Fenster (während des Debuggens, wählen Sie **Debuggen / Windows / parallele Stapel**).  
  
5.  Betrachten Sie die vierte Spalte von links, mit der Bezeichnung **Kategorie**. Die Threads werden in Kategorien klassifiziert.  
  
     Der erste in einem Prozess erstellte Thread wird als Hauptthread bezeichnet. Suchen Sie ihn in der Threadliste.  
  
6.  Mit der rechten Maustaste des Hauptthreads, und klicken Sie dann auf **zu Thread wechseln**.  
  
     Ein **im Unterbrechungsmodus** Fenster wird angezeigt. Sie werden darüber informiert, dass der Debugger keiner Code derzeit ausgeführt wird, die angezeigt werden können (da es sich um den Hauptthread handelt).   
  
7.  Betrachten Sie die **Aufrufliste** Fenster und die **Debugspeicherort** Symbolleiste.  
  
     Der Inhalt der **Aufrufliste** Fenster geändert haben. 

## <a name="bkmk_freeze"></a>Sperren und Entsperren der Threadausführung 

Sie können Einfrieren und reaktivieren (anhalten und fortsetzen) Threads zur Steuerung der Reihenfolge, in denen Threads Arbeit ausführen. Dadurch können Sie Parallelitätsprobleme wie Deadlocks und Racebedingungen.

> [!TIP]
> Wenn Sie verwenden möchten, führen einen einzelnen Thread ohne das Fixieren von anderen Threads (auch ein common Debugszenario), finden Sie unter [erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>So sperren und entsperren Sie Threads  
  
1.  In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **fixieren**.  
  
2.  Betrachten Sie die zweite Spalte (der aktuelle Thread-Spalte). Das Symbol "Anhalten" wird nun hier angezeigt. Diese Pausensymbol gibt an, dass der Thread gesperrt ist.  
  
3.  Anzeigen der **angehaltene Anzahl** Spalte durch Auswahl in der **Spalten** Liste.

    Der Unterbrechungszähler für den Thread lautet jetzt 1.  
  
4.  Mit der rechten Maustaste des gesperrten Threads, und klicken Sie dann auf **reaktivieren**.  
  
     Die Spalte mit dem aktuellen Thread und die **angehaltene Anzahl** Spalte ändern. 
  
## <a name="switching-the-to-another-thread"></a>Wechseln der an einen anderen Thread 
  
#### <a name="to-switch-threads"></a>So wechseln Sie zwischen Threads  
  
1.  In der **Threads** Fenster, überprüfen Sie die zweite Spalte von links (der aktuelle Thread-Spalte). Die Schaltfläche am Anfang dieser Spalte weist keinen Text bzw. kein Symbol auf.
  
2.  Betrachten Sie die Spalte mit dem aktuellen Thread, und beachten Sie, dass ein Thread einen gelben Pfeil verfügt. Der gelbe Pfeil gibt an, dass der Thread der aktuelle Thread ist (Dies ist die aktuelle Position des Zeigers Ausführung).
  
    Notieren Sie die Thread-ID-Nummer, in denen das aktuelle Symbol "Thread" angezeigt. Verschieben Sie das Symbol für den aktuellen Thread an einen anderen Thread, jedoch müssen Sie es platzieren zurück, wenn Sie fertig sind. 
  
3.  Mit der rechten Maustaste in einen anderen Thread aus, und klicken Sie dann auf **zu Thread wechseln**.  
  
4.  Betrachten Sie die **Aufrufliste** Fenster in der Quellcode-Editors. Der Inhalt hat sich geändert.  
  
5.  Betrachten Sie die **Debugspeicherort** Symbolleiste. Das Symbol für den aktuellen Thread hat dort geändert.  
  
6.  Wechseln Sie zu der **Debugspeicherort** Symbolleiste. Wählen Sie einen anderen Thread aus der **Thread** Liste.  
  
7.  Betrachten Sie die **Threads** Fenster. Das aktuelle Symbol "Thread" wurde geändert.  
  
8. Der Quellcode-Editor mit der Maustaste eines Threadmarker. Zeigen Sie im Kontextmenü auf **zu Thread wechseln** , und klicken Sie auf einen Threadnamen/eine Thread-ID.  
  
     Sie haben jetzt drei Möglichkeiten kennen gelernt ändern das Symbol für den aktuellen Thread an einen anderen Thread: Verwenden der **Threads** Fenster die **Thread** in Liste der **Debugspeicherort** Symbolleiste und die Threadmarker in der Quellcode-Editors.  
  
     Mit den Threadmarker können Sie nur zu Threads wechseln, die an der jeweiligen Position angehalten wurden. Mithilfe der **Threads** Fenster und **Debugspeicherort** Symbolleiste, die Sie an einen beliebigen Thread wechseln können.   
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
