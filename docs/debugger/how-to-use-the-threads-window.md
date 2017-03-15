---
title: "Gewusst wie: Verwenden des Fensters Threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.threads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Threading [Visual Studio], Debuggen"
  - "Thread.Name-Eigenschaft"
  - "Debugger, Threadfenster"
  - "SetThreadName-Funktion"
  - "Threadfenster"
  - "@TIB"
  - "Debuggen [Visual Studio], Threads"
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden des Fensters Threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Fenster **Threads** können Sie Threads in der gedebuggten Anwendung überprüfen und diese bearbeiten.  
  
 Das Fenster **Threads** enthält eine Tabelle, in der jede Zeile einen Thread in der Anwendung darstellt.  Standardmäßig sind in der Tabelle alle Threads in der Anwendung aufgeführt. Sie können die Liste jedoch filtern, sodass nur die gewünschten Threads angezeigt werden.  Jede Spalte enthält einen anderen Typ von Informationen.  Sie können auch einige Spalten ausblenden.  Wenn alle Spalten eingeblendet sind, werden die folgenden Informationen angezeigt \(von links nach rechts\):  
  
-   Die Flagspalte, in Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.  Weitere Informationen zum Kennzeichnen von Threads erhalten Sie unter [Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Die Spalte mit aktiven Threads, in der ein gelber Pfeil einen aktiven Thread anzeigt.  Konturen eines Pfeils geben den Thread an, in dem die Ausführung durch den Debugger unterbrochen wurde.  
  
-   Die Spalte **ID**, die die ID für jeden Thread enthält.  
  
-   Die Spalte **Verwaltete ID**, die die verwalteten IDs für verwaltete Threads enthält.  
  
-   Die Spalte **Kategorie**, in der Threads als Benutzeroberflächenthreads, Remoteprozeduraufruf\-Handler oder Arbeitsthreads kategorisiert werden.  In einer speziellen Kategorie wird der Hauptthread der Anwendung angegeben.  
  
-   Die Spalte **Name**, in der jeder Thread anhand seines Namens identifiziert wird, sofern ein solcher vorhanden ist \(andernfalls mit \<Kein Name\>\).  
  
-   Die Spalte **Speicherort**, in der angezeigt wird, wo der Thread ausgeführt wird.  Sie können diesen Speicherort erweitern, um die vollständige Aufrufliste für den Thread anzuzeigen.  
  
-   Die Spalte **Priorität**, in der die Priorität bzw. Rangfolge angezeigt wird, die den einzelnen Threads vom System zugewiesen wurde.  
  
-   Die Spalte **Affinitätsmaske**, die eine erweiterte Spalte darstellt, die normalerweise ausgeblendet ist.  In dieser Spalte wird die Prozessor\-Affinitätsmaske für jeden Thread angezeigt.  In einem Multiprozessorsystem bestimmt die Affinitätsmaske die Prozessoren, auf denen ein Thread ausgeführt werden kann.  
  
-   Die Spalte **Angehaltene Anzahl**, in der der Unterbrechungszähler angegeben ist.  Dieser Zähler bestimmt, ob ein Thread ausgeführt werden kann.  Eine Erläuterung des Unterbrechungszählers finden Sie in diesem Thema im Abschnitt "Sperren und Entsperren von Threads".  
  
-   Die Spalte **Prozessname**, die den Prozess aufführt, zu dem die einzelnen Threads gehören.  Diese Spalte kann hilfreich sein, wenn Sie mehrere Prozesse debuggen. Normalerweise ist sie jedoch ausgeblendet.  
  
### So zeigen Sie das Fenster Threads im Unterbrechungs\- oder Ausführmodus an  
  
-   Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie auf **Threads**.  
  
### So blenden Sie Spalten ein oder aus  
  
-   Klicken Sie am oberen Rand des Fensters **Threads** auf der Symbolleiste auf **Spalten**, und aktivieren bzw. deaktivieren Sie dann die Namen der anzuzeigenden bzw. auszublendenden Spalten.  
  
### So wechseln Sie den aktiven Thread  
  
-   Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf einen beliebigen Thread.  
  
    -   Klicken Sie mit der rechten Maustaste auf einen Thread, und klicken Sie auf **Zu Thread wechseln**.  
  
         Der gelbe Pfeil wird neben dem neuen aktiven Thread angezeigt.  Die grauen Konturen eines Pfeils geben den Thread, in dem der Debugger die Ausführung unterbrochen hat.  
  
## Gruppieren und Sortieren von Threads  
 Beim Gruppieren von Threads wird in der Tabelle eine Überschrift für jede Gruppe angezeigt.  Die Überschrift enthält eine Gruppenbeschreibung \(z. B. "Arbeitsthread" oder "Nicht gekennzeichnete Threads"\) und ein Strukturansicht\-Steuerelement.  Die einzelnen Threads jeder Gruppe werden unter der Gruppenüberschrift angezeigt.  Wenn Sie die einzelnen Threads einer Gruppe ausblenden möchten, können Sie die Gruppe mithilfe des Strukturansicht\-Steuerelements reduzieren.  
  
 Da die Gruppierung Vorrang gegenüber der Sortierung hat, können Sie Threads z. B. nach Kategorien gruppieren und anschließend in den einzelnen Kategorien nach ID sortieren.  
  
#### So sortieren Sie Threads  
  
1.  Klicken Sie auf der Symbolleiste oben im Fenster **Threads** auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
2.  Wenn Sie die Sortierreihenfolge umkehren möchten, klicken Sie erneut auf dieselbe Schaltfläche.  
  
     Threads, die am Anfang der Liste angezeigt wurden, werden nun am Ende der Liste aufgeführt.  
  
#### So gruppieren Sie Threads  
  
-   Klicken Sie auf der Symbolleiste des Fensters **Threads** auf die Liste **Gruppieren nach**, und klicken Sie anschließend auf die Kriterien, anhand derer Sie Threads gruppieren möchten.  
  
#### So sortieren Sie Threads innerhalb von Gruppen  
  
1.  Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf die Liste **Gruppieren nach**, und klicken Sie anschließend auf die Kriterien, anhand derer Sie Threads gruppieren möchten.  
  
2.  Klicken Sie im Fenster **Threads** auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
#### So erweitern oder reduzieren Sie alle Gruppen  
  
-   Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf **Gruppen erweitern** oder **Gruppen reduzieren**.  
  
## Suchen nach bestimmten Threads  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie nach Threads suchen, die einer bestimmten Zeichenfolge entsprechen.  Wenn Sie im Fenster **Threads** nach Threads suchen, werden alle Threads angezeigt, die der Suchzeichenfolge in den einzelnen Spalten entsprechen.  Zu diesen Informationen zählt der Threadspeicherort, der am oberen Rand der Aufrufliste in der Spalte **Speicherort** angezeigt wird.  Standardmäßig wird jedoch nicht die vollständige Aufrufliste durchsucht.  
  
#### So suchen Sie nach bestimmten Threads  
  
-   Wechseln Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** in das Feld **Suchen**, und führen Sie Folgendes aus:  
  
    -   Geben Sie eine Suchzeichenfolge ein, und drücken Sie dann die EINGABETASTE.  
  
         \- oder \-  
  
    -   Klicken Sie auf die Dropdownliste neben dem Feld **Suchen**, und wählen Sie eine Suchzeichenfolge aus einem früheren Suchvorgang aus.  
  
-   \(Optional\) Wenn bei der Suche die vollständige Aufrufliste berücksichtigt werden soll, wählen Sie **Aufrufliste suchen** aus.  
  
## Sperren und Entsperren von Threads  
 Wenn ein Thread eingefroren ist, wird die Threadausführung vom System auch dann nicht gestartet, wenn Ressourcen verfügbar sind.  
  
 Im systemeigenen Code kann die Ausführung von Threads unterbrochen und fortgesetzt werden, indem die Windows\-Funktionen `SuspendThread` und `ResumeThread` oder die MFC\-Funktionen [CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md) und [CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md) aufgerufen werden.  Wenn Sie `SuspendThread` oder `ResumeThread` aufrufen, ändern Sie den *Unterbrechungszähler*, der im Fenster **Threads** angezeigt wird.  Wenn Sie jedoch einen systemeigenen Thread einfrieren oder reaktivieren, wird dadurch der Unterbrechungszähler nicht geändert.  Im systemeigenen Code kann ein Thread nur ausgeführt werden, wenn er reaktiviert ist und sein Unterbrechungszähler den Wert 0 aufweist.  
  
 In verwaltetem Code hat das Einfrieren oder Reaktivieren keinen Einfluss auf den Wert des Unterbrechungszählers.  In verwaltetem Code hat ein eingefrorener Thread den Unterbrechungszähler 1 auf.  In systemeigenem Code hat der Unterbrechungszähler eines eingefrorenen Threads den Wert 0, es sei denn, seine Ausführung wurde durch einen `SuspendThread`\-Aufruf unterbrochen.  
  
> [!NOTE]
>  Beim Debuggen eines Aufrufs vom systemeigenen Code in den verwalteten Code wird der verwaltete Code im selben physischen Thread ausgeführt wie der systemeigene Code, durch den er aufgerufen wurde.  Durch Unterbrechen oder Sperren des systemeigenen Threads wird auch der verwaltete Code gesperrt.  
  
#### So können Sie die Ausführung eines Threads einfrieren oder reaktivieren  
  
-   Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf **Threads einfrieren** oder **Threads reaktivieren**.  
  
     Dieser Vorgang wirkt sich nur auf Threads aus, die im Fenster **Threads** ausgewählt sind.  
  
## Anzeigen von gekennzeichneten Threads  
 Einen Thread, der besondere Aufmerksamkeit erhalten soll, können Sie kennzeichnen, indem sie ihn im Fenster **Threads** mit einem Symbol markieren.  Weitere Informationen finden Sie unter [Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md).  Im Fenster "Threads" können Sie festlegen, dass alle Threads oder nur die gekennzeichneten Threads angezeigt werden.  
  
#### So zeigen Sie nur gekennzeichnete Threads an  
  
-   Klicken Sie in der oberen linken Ecke des **Threadfensters** auf die Kennzeichnungsschaltfläche.  
  
## Anzeigen von Threadaufruflisten und Wechseln zwischen Rahmen  
 In einem Multithreadprogramm verfügt jeder Thread über eine eigene Aufrufliste.  Das Fenster **Threads** bietet eine benutzerfreundliche Möglichkeit, diese Aufruflisten anzuzeigen.  
  
#### So zeigen Sie die Aufrufliste eines Threads an  
  
-   Klicken Sie in der Spalte **Speicherort** auf das umgekehrte Dreieck neben dem Threadspeicherort.  
  
     Der Speicherort wird erweitert, und die Aufrufliste für den Thread wird angezeigt.  
  
#### So können Sie die Aufruflisten aller Threads anzeigen oder reduzieren  
  
-   Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf **Aufruflisten erweitern** oder auf **Aufruflisten reduzieren**.  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md)