---
title: "Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Multithread-Debugging, Exemplarische Vorgehensweise"
  - "Exemplarische Vorgehensweisen, Multithread-Debugging"
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] bietet ein optimiertes **Threadfenster** und weitere Verbesserungen der Benutzeroberfläche, die das Debuggen von Multithreadanwendungen erleichtern.  Diese exemplarische Vorgehensweise macht Sie in nur wenigen Minuten mit den neuen Benutzeroberflächenfeatures vertraut, die zum Debuggen von Multithreadanwendungen verwendet werden können.  
  
 Um mit dieser exemplarischen Vorgehensweise zu beginnen, benötigen Sie ein Multithreadanwendungsprojekt.  Befolgen Sie die hier aufgeführten Schritte, um das Projekt zu erstellen.  
  
#### So erstellen Sie das Projekt für die exemplarische Vorgehensweise  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** aus, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Klicken Sie im Feld **Projekttypen** auf die gewünschte Programmiersprache: **Visual Basic**, **Visual C\#** oder **Visual C\+\+**.  
  
3.  Wählen Sie im Feld **Vorlagen** die Option **Konsolenanwendung** oder **CLR\-Konsolenanwendung** aus.  
  
4.  Geben Sie im Feld **Name** den Namen MyThreadWalkthroughApp ein.  
  
5.  Klicken Sie auf **OK**.  
  
     Ein neues Konsolenprojekt wird angezeigt.  Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt.  Abhängig von der ausgewählten Programmiersprache hat die Quelldatei die Bezeichnung Module1.vb, Program.cs oder MyThreadWalkthroughApp.cpp.  
  
6.  Löschen Sie den in der Quelldatei enthaltenen Code, indem Sie ihn durch den Beispielcode ersetzen, der im Abschnitt "Erstellen eines Threads" unter dem Thema [Creating Threads and Passing Data at Start Time](../Topic/Creating%20Threads%20and%20Passing%20Data%20at%20Start%20Time.md) aufgeführt ist.  
  
7.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### So beginnen Sie mit der exemplarischen Vorgehensweise  
  
-   Suchen Sie im Quellcodefenster nach folgendem Code:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```c#  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### So starten Sie das Debuggen  
  
1.  Klicken Sie mit der rechten Maustaste auf die `Console.WriteLine`\-Anweisung, zeigen Sie auf **Haltepunkt**, und klicken Sie dann auf **Haltepunkt einfügen**.  
  
     Innerhalb des Bundstegs auf der linken Seite des Quellcodefensters wird eine rote Kugel angezeigt.  Diese Kugel zeigt an, dass an dieser Stelle jetzt ein Haltepunkt festgelegt wurde.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Der Debugvorgang beginnt, die Konsolenanwendung wird gestartet und hält dann am Haltepunkt an.  
  
3.  Wenn sich der Fokus zu diesem Zeitpunkt im Fenster der Konsolenanwendung befindet, klicken Sie in das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Fenster, um den Fokus wieder an [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zurückzugeben.  
  
4.  Suchen Sie im Quellcodefenster die Zeile, die den folgenden Code enthält:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```c#  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
#### So ermitteln Sie den Threadmarker  
  
1.  Klicken Sie mit der rechten Maustaste in das Fenster **Threads**, und klicken Sie dann auf **Threads in Quelle anzeigen**.  
  
2.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters.  In dieser Zeile sehen Sie ein Symbol, das zwei Fäden ähnelt.  Der eine ist rot und der andere blau.  Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.  Der Thread wurde möglicherweise an dieser Position angehalten.  
  
3.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker.  Ein DataTip wird angezeigt.  Anhand des DataTips erfahren Sie den Namen und die Thread\-ID jedes angehaltenen Threads.  In diesem Fall gibt es nur einen Thread, dessen Name wahrscheinlich `<noname>` lautet.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Threadmarker.  Beachten Sie die Auswahlen im Kontextmenü.  
  
 Dieses Symbol ist ein *Threadmarker*:  
  
 ![Thread&#45;Marker](../debugger/media/threadmarker.png "ThreadMarker")  
  
## Kennzeichnen von Threads und Aufheben der Kennzeichnung  
 In [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] können Sie Threads kennzeichnen, die besondere Aufmerksamkeit erfordern.  Das Kennzeichnen von Threads bietet eine gute Möglichkeit, wichtige Threads nachzuverfolgen und unwichtige Threads zu ignorieren.  
  
#### So kennzeichnen Sie Threads  
  
1.  Zeigen Sie im Menü **Ansicht** auf **Symbolleisten**.  
  
     Stellen Sie sicher, dass die Symbolleiste **Debugspeicherort** ausgewählt ist.  
  
2.  Klicken Sie auf der Symbolleiste **Debugspeicherort** auf die Liste **Thread**.  
  
    > [!NOTE]
    >  Diese Symbolleiste erkennen Sie an den drei gut sichtbaren Listen: **Prozess**, **Thread** und **Stapelrahmen**.  
  
3.  Beachten Sie, wie viele Threads in der Liste angezeigt werden.  
  
4.  Wechseln Sie zurück zum Quellcodefenster, und klicken Sie wieder mit der rechten Maustaste auf den **Threadmarker**.  
  
5.  Zeigen Sie im Kontextmenü auf **Kennzeichner**, und klicken Sie dann auf den Threadnamen und die ID.  
  
6.  Wechseln Sie zurück zur Symbolleiste **Debugspeicherort**, und klicken Sie erneut auf die Liste **Thread**.  
  
     Jetzt wird nur der gekennzeichnete Thread in der Liste angezeigt.  Die Kennzeichnungsschaltfläche, die sich direkt rechts neben der Liste **Thread** befindet.  Das Kennzeichnungssymbol auf der Schaltfläche war zuvor abgeblendet.  Jetzt wird es in einem reinen, hellen Rot angezeigt.  
  
7.  Zeigen Sie mit dem Mauszeiger auf das Kennzeichnungssymbol.  
  
     Ein Popupfenster wird eingeblendet.  In diesem Popupfenster ist angegeben, in welchem Modus sich die Liste **Thread** befindet: **Nur gekennzeichnete Threads anzeigen**.  
  
8.  Klicken Sie auf die Kennzeichnungsschaltfläche, um wieder zum Modus **Alle Threads anzeigen** zu wechseln.  
  
9. Klicken Sie erneut auf die Liste **Thread**, und überprüfen Sie, ob jetzt wieder alle Threads angezeigt werden.  
  
10. Klicken Sie auf die Kennzeichnungsschaltfläche, um zurück zu **Nur gekennzeichnete Threads anzeigen** zu wechseln.  
  
11. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie auf **Threads**.  
  
     Das Fenster **Threads** wird angezeigt.  Ein Thread ist mit einem deutlich erkennbaren Kennzeichnungssymbol versehen.  
  
12. Klicken Sie im Quellcodefenster mit der rechten Maustaste erneut auf den Threadmarker.  
  
     Beachten Sie, welche Auswahlen jetzt im Kontextmenü verfügbar sind.  Anstelle von **Kennzeichner** sehen Sie jetzt **Flag entfernen**.  Klicken Sie nicht auf **Flag entfernen**.  
  
13. Fahren Sie mit dem nächsten Verfahren fort, in dem die Kennzeichnung von Threads aufgehoben wird.  
  
#### So heben Sie die Kennzeichnung von Threads auf  
  
1.  Klicken Sie im **Threadfenster** mit der rechten Maustaste auf die Zeile, die dem gekennzeichneten Thread entspricht.  
  
     Ein Kontextmenü wird angezeigt.  Das Menü bietet die Optionen **Flag entfernen** und **Kennzeichnung aller Threads aufheben**.  
  
2.  Um die Kennzeichnung des Threads aufzuheben, klicken Sie auf **Flag entfernen**.  
  
3.  Klicken Sie auf das rote Kennzeichnungssymbol.  
  
4.  Überprüfen Sie erneut die Symbolleiste **Debugspeicherort**.  Die Kennzeichnungsschaltfläche ist wieder abgeblendet.  Sie haben die Kennzeichnung des einzigen gekennzeichneten Threads aufgehoben.  Da keine gekennzeichneten Threads vorhanden sind, wurde die Symbolleiste wieder in den Modus **Alle Threads anzeigen** zurückversetzt.  Klicken Sie auf die Liste **Thread**, und stellen Sie sicher, dass alle Threads angezeigt werden.  
  
5.  Wechseln Sie zurück zum **Threadfenster**, und überprüfen Sie die Informationsspalten.  
  
     Am Anfang der einzelnen Spalten befinden sich Schaltflächen. Die meisten Schaltflächen sind mit einem Titel versehen, an dem die Spalte erkennbar ist.  Die erste Spalte auf der linken Seite hat jedoch keinen Titel.  Sie verfügt stattdessen über ein Symbol, das die Umrisslinie eines Flags darstellt.  Sie werden bemerken, dass jede Zeile der Threadliste dasselbe Umrisssymbol enthält.  Dies bedeutet, dass die Kennzeichnung des Threads aufgehoben ist.  
  
6.  Klicken Sie für zwei Threads in der Liste, den zweiten und dritten von unten, auf den Umriss des Flags.  
  
     Die Kennzeichensymbole werden in der Volltonfarbe Rot und nicht als leere Umrisslinien dargestellt.  
  
7.  Klicken Sie auf die Schaltfläche oben in der Kennzeichenspalte.  
  
     Die Reihenfolge der Threadliste wurde geändert, als Sie auf die Schaltfläche geklickt haben.  Die Threadliste ist jetzt neu sortiert, und die gekennzeichneten Threads befinden sich am Anfang.  
  
8.  Klicken Sie erneut auf die Schaltfläche am Anfang der Kennzeichenspalte.  
  
     Die Sortierreihenfolge wurde wieder geändert.  
  
## Weitere Informationen zum Threadfenster  
  
#### Weitere Informationen zum Threadfenster  
  
1.  Überprüfen Sie im **Threadfenster** die dritte Spalte von links.  Die Schaltfläche am Anfang dieser Spalte hat die Beschriftung **ID**.  
  
2.  Klicken Sie auf **ID**.  
  
     Die Threadliste wird jetzt nach Thread\-ID sortiert.  
  
3.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Thread in der Liste.  Klicken Sie im Kontextmenü auf **Hexadezimale Anzeige**.  
  
     Das Format der Thread\-IDs wird geändert.  
  
4.  Zeigen Sie mit dem Mauszeiger auf einen beliebigen Thread in der Liste.  
  
     Nach einer kurzen Verzögerung wird ein DataTip eingeblendet.  Er enthält eine teilweise Aufrufliste für den Thread.  
  
5.  Beachten Sie die vierte Spalte von links mit der Bezeichnung **Kategorie**.  Die Threads werden in Kategorien klassifiziert.  
  
     Der erste in einem Prozess erstellte Thread wird als Hauptthread bezeichnet.  Suchen Sie ihn in der Threadliste.  
  
6.  Klicken Sie mit der rechten Maustaste auf den Hauptthread, und klicken Sie dann auf **Zu Thread wechseln**.  
  
     Ein Warnungsdialogfeld wird angezeigt.  Es enthält den Hinweis, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] keinen Quellcode für den Hauptthread anzeigen kann.  
  
     Klicken Sie auf **OK**.  
  
7.  Überprüfen Sie das Fenster **Aufrufliste** und die Symbolleiste **Debugspeicherort**.  
  
     Der Inhalt des Fensters **Aufrufliste** wurde geändert.  
  
## Wechseln des aktiven Threads  
  
#### So wechseln Sie zwischen Threads  
  
1.  Überprüfen Sie im **Threadfenster** die zweite Spalte von links.  Die Schaltfläche am Anfang dieser Spalte weist keinen Text bzw. kein Symbol auf.  Diese Spalte ist die Spalte mit dem **aktiven Thread**.  
  
2.  Beachten Sie, dass ein Thread in der Spalte mit dem **aktiven Thread** über einen gelben Pfeil verfügt.  Dies ist der *Indikator für den aktiven Thread*.  
  
3.  Notieren Sie sich die ID des Threads, der durch den Indikator für den aktiven Thread gekennzeichnet ist.  Sie verschieben den Indikator für den aktiven Thread auf einen anderen Thread, müssen ihn nach Beendigung jedoch wieder an die frühere Position zurückversetzen.  
  
4.  Klicken Sie mit der rechten Maustaste auf einen anderen Thread, und klicken Sie dann auf **Zu Thread wechseln**.  
  
5.  Überprüfen Sie das Fenster **Aufrufliste** im Quellcodefenster.  Der Inhalt hat sich geändert.  
  
6.  Überprüfen Sie die Symbolleiste **Debugspeicherort**.  Der aktive Thread wurde auch dort geändert.  
  
7.  Wechseln Sie zur Symbolleiste **Debugspeicherort**.  Klicken Sie auf das Feld **Thread**, und wählen Sie einen anderen Thread aus der Dropdownliste aus.  
  
8.  Überprüfen Sie das **Threadfenster**.  Der Indikator für den aktiven Thread wurde geändert.  
  
9. Klicken Sie im Quellcodefenster mit der rechten Maustaste auf einen Threadmarker.  Zeigen Sie im Kontextmenü auf **Wechseln zu**, und klicken Sie auf einen Threadnamen\/eine Thread\-ID.  
  
     Sie haben jetzt drei Möglichkeiten kennen gelernt, wie Sie den aktiven Thread wechseln: über das **Threadfenster**, über das Feld **Thread** auf der Symbolleiste **Debugspeicherort** sowie mithilfe des Indikators für den aktiven Thread im Quellcodefenster.  
  
     Mit dem Threadindikator können Sie nur zu Threads wechseln, die an der jeweiligen Position angehalten wurden.  Über das **Threadfenster** und die Symbolleiste **Debugspeicherort** können Sie zu jedem beliebigen Thread wechseln.  
  
## Sperren und Entsperren der Threadausführung  
  
#### So sperren und entsperren Sie Threads  
  
1.  Klicken Sie im **Threadfenster** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **Sperren**.  
  
2.  Beachten Sie die Spalte mit dem aktiven Thread.  Jetzt wird dort das Paar senkrechter Striche angezeigt.  Diese beiden blauen Striche zeigen an, dass der Thread gesperrt ist.  
  
3.  Überprüfen Sie die Spalte **Unterbrechen**.  Der Unterbrechungszähler für den Thread lautet jetzt 1.  
  
4.  Klicken Sie mit der rechten Maustaste auf den gesperrten Thread, und klicken Sie dann auf **Entsperren**.  
  
     Die Spalte mit dem aktiven Thread und die Spalte **Unterbrechen** werden geändert.  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)