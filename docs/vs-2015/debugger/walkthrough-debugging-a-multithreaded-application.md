---
title: 'Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d598cc245421aafb05cbf91fe2b7a95e39564a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444318"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] bietet ein optimiertes **Threads** und weitere Verbesserungen zum Debuggen von Multithreadanwendungen erleichtern der Benutzeroberfläche. Diese exemplarische Vorgehensweise macht Sie in nur wenigen Minuten mit den neuen Benutzeroberflächenfunktionen vertraut, die zum Debuggen von Multithreadanwendungen verwendet werden können.  
  
 Um mit dieser exemplarischen Vorgehensweise zu beginnen, benötigen Sie ein Multithreadanwendungsprojekt. Befolgen Sie die hier aufgeführten Schritte, um das Projekt zu erstellen.  
  
#### <a name="to-create-the-walkthrough-project"></a>So erstellen Sie das Projekt für die exemplarische Vorgehensweise  
  
1. Auf der **Datei** Menü wählen **neu** , und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2. In der **Projekttyp**s Klicken Sie auf der Sprache Ihrer Wahl: **Visual Basic**, **Visual C#** , oder **Visual C++**.  
  
3. In der **Vorlagen** wählen **Konsolenanwendung** oder **CLR-Konsolenanwendung**.  
  
4. In der **Namen** geben den Namen MyThreadWalkthroughApp ein.  
  
5. Klicken Sie auf **OK**.  
  
     Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der ausgewählten Programmiersprache hat die Quelldatei die Bezeichnung Module1.vb, Program.cs oder MyThreadWalkthroughApp.cpp.  
  
6. Löschen Sie den Code, der in der Quelldatei angezeigt wird, und Ersetzen Sie ihn durch den Beispielcode, der im Abschnitt "Erstellen eines Threads" des Themas angezeigt wird [Erstellen von Threads und übergeben von Daten zur Startzeit](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### <a name="to-begin-the-walkthrough"></a>So beginnen Sie mit der exemplarischen Vorgehensweise  
  
- Suchen Sie im Quellcodefenster nach folgendem Code:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>So starten Sie das Debuggen  
  
1. Mit der rechten Maustaste die `Console.WriteLine` -Anweisung, zeigen Sie auf **Haltepunkt** , und klicken Sie dann auf **Haltepunkt einfügen**.  
  
     Innerhalb des Bundstegs auf der linken Seite des Quellcodefensters wird eine rote Kugel angezeigt. Diese Kugel zeigt an, dass an dieser Stelle jetzt ein Haltepunkt festgelegt wurde.  
  
2. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Der Debugvorgang beginnt, die Konsolenanwendung wird gestartet und hält dann am Haltepunkt an.  
  
3. Wenn sich der Fokus zu diesem Zeitpunkt im Fenster der Konsolenanwendung befindet, klicken Sie in das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Fenster, um den Fokus wieder an [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zurückzugeben.  
  
4. Suchen Sie im Quellcodefenster die Zeile, die den folgenden Code enthält:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>So ermitteln Sie den Threadmarker  
  
1. Mit der rechten Maustaste den **Threads** Fenster, klicken Sie dann auf **Threads in Quelle anzeigen**.  
  
2. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie ein Symbol, das zwei Fäden ähnelt. Der eine ist rot und der andere blau. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde. Der Thread wurde möglicherweise an dieser Position angehalten.  
  
3. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads. In diesem Fall gibt es nur einen Thread, dessen Name wahrscheinlich `<noname>` lautet.  
  
4. Klicken Sie mit der rechten Maustaste auf den Threadmarker. Beachten Sie die Auswahlen im Kontextmenü.  
  
   Dieses Symbol ist ein *Threadmarker*:  
  
   ![Thread-Marker](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung  
 In [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] können Sie Threads kennzeichnen, die besondere Aufmerksamkeit erfordern. Das Kennzeichnen von Threads bietet eine gute Möglichkeit, wichtige Threads nachzuverfolgen und unwichtige Threads zu ignorieren.  
  
#### <a name="to-flag-threads"></a>So kennzeichnen Sie Threads  
  
1. Auf **Ansicht** Startmenü **Symbolleisten**.  
  
     Stellen Sie sicher, dass die **Debugspeicherort** Symbolleiste ausgewählt ist.  
  
2. Wechseln Sie zu der **Debugspeicherort** Symbolleiste, und klicken Sie auf die **Thread** Liste.  
  
    > [!NOTE]
    > Sie können diese Symbolleiste erkennen, drei gut sichtbaren Listen: **Prozess**, **Thread**, und **Stapelrahmen**.  
  
3. Beachten Sie, wie viele Threads in der Liste angezeigt werden.  
  
4. Wechseln Sie zurück zum Quellcodefenster, und mit der rechten Maustaste die **Thread** Marker erneut aus.  
  
5. Zeigen Sie im Kontextmenü auf **Flag**, und klicken Sie dann auf den Threadnamen und die ID-Nummer.  
  
6. Wechseln Sie zurück zur **Debugspeicherort** Symbolleiste, und klicken Sie auf die **Thread** erneut auflisten.  
  
     Jetzt wird nur der gekennzeichnete Thread in der Liste angezeigt. Die Kennzeichnungsschaltfläche, die nur auf der rechten Seite des der **Thread** Liste. Das Kennzeichnungssymbol auf der Schaltfläche war zuvor abgeblendet. Jetzt wird es in einem reinen, hellen Rot angezeigt.  
  
7. Zeigen Sie mit dem Mauszeiger auf das Kennzeichnungssymbol.  
  
     Ein Popupfenster wird eingeblendet. Diesem Popupfenster ist angegeben, in welchem Modus der **Thread** Liste finden Sie in: **Nur gekennzeichnete Threads anzeigen**.  
  
8. Klicken Sie auf die Schaltfläche "kennzeichnen", um zurück zu wechseln **alle Threads anzeigen** Modus.  
  
9. Klicken Sie auf die **Thread** erneut aus, und stellen Sie sicher, dass jetzt wieder alle Threads angezeigt werden.  
  
10. Klicken Sie auf die Schaltfläche "kennzeichnen", um zurück zu wechseln **nur gekennzeichnete Threads anzeigen**.  
  
11. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Threads**.  
  
     Die **Threads** Fenster wird angezeigt. Ein Thread ist mit einem deutlich erkennbaren Kennzeichnungssymbol versehen.  
  
12. Klicken Sie im Quellcodefenster mit der rechten Maustaste erneut auf den Threadmarker.  
  
     Beachten Sie, welche Auswahlen jetzt im Kontextmenü verfügbar sind. Anstelle von **Flag**, sehen Sie jetzt **Flag**. Klicken Sie nicht auf **Flag**.  
  
13. Fahren Sie mit dem nächsten Verfahren fort, in dem die Kennzeichnung von Threads aufgehoben wird.  
  
#### <a name="to-unflag-threads"></a>So heben Sie die Kennzeichnung von Threads auf  
  
1. Auf der **Threads** Fenster mit der rechten Maustaste in der Zeile, die dem gekennzeichneten Thread entspricht.  
  
     Ein Kontextmenü wird angezeigt. Bietet die Optionen **Flag** und **Kennzeichnung aller Threads aufheben**.  
  
2. Um den Thread Kennzeichnung aufzuheben, klicken Sie auf **Flag**.  
  
3. Klicken Sie auf das rote Kennzeichnungssymbol.  
  
4. Sehen Sie sich die **Debugspeicherort** Symbolleiste erneut. Die Kennzeichnungsschaltfläche ist wieder abgeblendet. Sie haben die Kennzeichnung des einzigen gekennzeichneten Threads aufgehoben. Da keine gekennzeichneten Threads vorhanden sind, die Symbolleiste ist wieder auf **alle Threads anzeigen** Modus. Klicken Sie auf die **Thread** aus, und stellen Sie sicher, dass Sie alle Threads angezeigt werden.  
  
5. Wechseln Sie zurück zu den **Threads** Fenster, und untersuchen Sie die Informationsspalten.  
  
     Am Anfang der einzelnen Spalten befinden sich Schaltflächen. Die meisten Schaltflächen sind mit einem Titel versehen, an dem die Spalte erkennbar ist. Die erste Spalte auf der linken Seite hat jedoch keinen Titel. Sie verfügt stattdessen über ein Symbol, das die Umrisslinie eines Flags darstellt. Sie werden bemerken, dass jede Zeile der Threadliste dasselbe Umrisssymbol enthält. Dies bedeutet, dass die Kennzeichnung des Threads aufgehoben ist.  
  
6. Klicken Sie für zwei Threads in der Liste, den zweiten und dritten von unten, auf den Umriss des Flags.  
  
     Die Kennzeichensymbole werden in der Volltonfarbe Rot und nicht als leere Umrisslinien dargestellt.  
  
7. Klicken Sie auf die Schaltfläche oben in der Kennzeichenspalte.  
  
     Die Reihenfolge der Threadliste wurde geändert, als Sie auf die Schaltfläche geklickt haben. Die Threadliste ist jetzt neu sortiert, und die gekennzeichneten Threads befinden sich am Anfang.  
  
8. Klicken Sie erneut auf die Schaltfläche am Anfang der Kennzeichenspalte.  
  
     Die Sortierreihenfolge wurde wieder geändert.  
  
## <a name="more-about-the-threads-window"></a>Weitere Informationen zum Threadfenster  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Weitere Informationen zum Threadfenster  
  
1. In der **Threads** Fenster, überprüfen Sie die dritte Spalte von links. Die Schaltfläche am Anfang dieser Spalte daneben **ID**.  
  
2. Klicken Sie auf **ID**.  
  
     Die Threadliste wird jetzt nach Thread-ID sortiert.  
  
3. Klicken Sie mit der rechten Maustaste auf einen beliebigen Thread in der Liste. Klicken Sie im Kontextmenü auf **Hexadezimale Anzeige**.  
  
     Das Format der Thread-IDs wird geändert.  
  
4. Zeigen Sie mit dem Mauszeiger auf einen beliebigen Thread in der Liste.  
  
     Nach einer kurzen Verzögerung wird ein DataTip eingeblendet. Er enthält eine teilweise Aufrufliste für den Thread.  
  
5. Betrachten Sie die vierte Spalte von links, mit der Bezeichnung **Kategorie**. Die Threads werden in Kategorien klassifiziert.  
  
     Der erste in einem Prozess erstellte Thread wird als Hauptthread bezeichnet. Suchen Sie ihn in der Threadliste.  
  
6. Mit der rechten Maustaste in des Hauptthreads, und klicken Sie dann auf **zu Thread wechseln**.  
  
     Ein Warnungsdialogfeld wird angezeigt. Es enthält den Hinweis, dass [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] keinen Quellcode für den Hauptthread anzeigen kann.  
  
     Klicken Sie auf **OK**.  
  
7. Sehen Sie sich die **Aufrufliste** Fenster und die **Debugspeicherort** Symbolleiste.  
  
     Den Inhalt der **Aufrufliste** Fenster geändert haben.  
  
## <a name="switching-the-active-thread"></a>Wechseln des aktiven Threads  
  
#### <a name="to-switch-threads"></a>So wechseln Sie zwischen Threads  
  
1. In der **Threads** Fenster, überprüfen Sie die zweite Spalte von links. Die Schaltfläche am Anfang dieser Spalte weist keinen Text bzw. kein Symbol auf. Diese Spalte ist der **aktiven Thread** Spalte.  
  
2. Sehen Sie sich die **aktiven Thread** Spalten- und beachten Sie, dass ein Thread einen gelben Pfeil. Dies ist die *Indikator für den aktiven Thread*.  
  
3. Notieren Sie sich die ID des Threads, der durch den Indikator für den aktiven Thread gekennzeichnet ist. Sie verschieben den Indikator für den aktiven Thread auf einen anderen Thread, müssen ihn nach Beendigung jedoch wieder an die frühere Position zurückversetzen.  
  
4. Mit der rechten Maustaste in einem anderen Thread aus, und klicken Sie dann auf **zu Thread wechseln**.  
  
5. Sehen Sie sich die **Aufrufliste** Fenster im Quellcodefenster. Der Inhalt hat sich geändert.  
  
6. Sehen Sie sich die **Debugspeicherort** Symbolleiste. Der aktive Thread wurde auch dort geändert.  
  
7. Wechseln Sie zu der **Debugspeicherort** Symbolleiste. Klicken Sie auf die **Thread** ein, und wählen Sie einen anderen Thread aus der Dropdown-Liste.  
  
8. Sehen Sie sich die **Threads** Fenster. Der Indikator für den aktiven Thread wurde geändert.  
  
9. Klicken Sie im Quellcodefenster mit der rechten Maustaste auf einen Threadmarker. Zeigen Sie im Kontextmenü auf **wechseln Sie zur** , und klicken Sie auf einen Threadnamen/eine Thread-ID.  
  
     Sie haben nun gesehen, drei Möglichkeiten, den aktiven Thread: Verwenden der **Threads** Fenster die **Thread** im Feld der **Debugspeicherort** Symbolleiste und den Indikator für den Thread in der Datenquellen-Fenster.  
  
     Mit dem Threadindikator können Sie nur zu Threads wechseln, die an der jeweiligen Position angehalten wurden. Über das **Threadfenster** und die Symbolleiste **Debugspeicherort** können Sie zu jedem beliebigen Thread wechseln.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Sperren und Entsperren der Threadausführung  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>So sperren und entsperren Sie Threads  
  
1. In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **fixieren**.  
  
2. Beachten Sie die Spalte mit dem aktiven Thread. Jetzt wird dort das Paar senkrechter Striche angezeigt. Diese beiden blauen Striche zeigen an, dass der Thread gesperrt ist.  
  
3. Sehen Sie sich die **Suspend** Spalte. Der Unterbrechungszähler für den Thread lautet jetzt 1.  
  
4. Mit der rechten Maustaste in des gesperrten Threads, und klicken Sie dann auf **reaktivieren**.  
  
     Die Spalte mit aktiven Threads und die **Suspend** ändert sich die Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens](../debugger/how-to-switch-to-another-thread-while-debugging.md)
