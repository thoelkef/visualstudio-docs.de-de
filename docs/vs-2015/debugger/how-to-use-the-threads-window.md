---
title: 'Gewusst wie: Verwenden des Fensters "Threads" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824255"
---
# <a name="how-to-use-the-threads-window"></a>Gewusst wie: Verwenden des Fensters Threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Fenster **Threads** können Sie Threads in der Anwendung, die Sie Debuggen, überprüfen und bearbeiten.  
  
 Das Fenster **Threads** enthält eine Tabelle, in der jede Zeile einen Thread in der Anwendung darstellt. Standardmäßig sind in der Tabelle alle Threads in der Anwendung aufgeführt. Sie können die Liste jedoch filtern, sodass nur die gewünschten Threads angezeigt werden. Jede Spalte enthält einen anderen Typ von Informationen. Sie können auch einige Spalten ausblenden. Wenn alle Spalten eingeblendet sind, werden die folgenden Informationen angezeigt (von links nach rechts):  
  
- Die Flagspalte, in Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll. Weitere Informationen zum Markieren eines Threads finden Sie unter Gewusst [wie: markieren und](../debugger/how-to-flag-and-unflag-threads.md)Aufheben der Flag von Threads.  
  
- Die Spalte mit aktiven Threads, in der ein gelber Pfeil einen aktiven Thread anzeigt. Konturen eines Pfeils geben den Thread an, in dem die Ausführung durch den Debugger unterbrochen wurde.  
  
- Die **ID** -Spalte, die die Identifikationsnummer für jeden Thread enthält.  
  
- Die **verwaltete ID** -Spalte, die die verwalteten Identifikationsnummern für verwaltete Threads enthält.  
  
- Die **Kategoriespalte** , die Threads als Benutzeroberflächenthreads, Remote Prozedur aufrufshandler oder Arbeitsthreads kategorisiert. In einer speziellen Kategorie wird der Hauptthread der Anwendung angegeben.  
  
- Die **Name** -Spalte, die jeden Thread anhand des Namens identifiziert, wenn er über einen oder einen verfügt \<No Name> .  
  
- Die **Location** -Spalte, die anzeigt, wo der Thread ausgeführt wird. Sie können diesen Speicherort erweitern, um die vollständige Aufrufliste für den Thread anzuzeigen.  
  
- Die **Prioritäts** Spalte, die die Priorität oder Rangfolge enthält, die das System jedem Thread zugewiesen hat.  
  
- Die **Affinitäts Masken** Spalte, bei der es sich um eine erweiterte Spalte handelt, die normalerweise ausgeblendet ist. In dieser Spalte wird die Prozessor-Affinitätsmaske für jeden Thread angezeigt. In einem Multiprozessorsystem bestimmt die Affinitätsmaske die Prozessoren, auf denen ein Thread ausgeführt werden kann.  
  
- Die angehaltene **Anzahl** Spalte, die die Anzahl angehaltene Spalten enthält. Dieser Zähler bestimmt, ob ein Thread ausgeführt werden kann. Eine Erläuterung des Unterbrechungszählers finden Sie in diesem Thema im Abschnitt "Sperren und Entsperren von Threads".  
  
- Die Spalte **Prozess Name** , die den Prozess enthält, zu dem der jeweilige Thread gehört. Diese Spalte kann hilfreich sein, wenn Sie mehrere Prozesse debuggen. Normalerweise ist sie jedoch ausgeblendet.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>So zeigen Sie das Fenster Threads im Unterbrechungs- oder Ausführmodus an  
  
- Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus  
  
- Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf **Spalten**, und wählen Sie den Namen der Spalte aus, die Sie anzeigen oder ausblenden möchten, oder löschen Sie ihn.  
  
### <a name="to-switch-the-active-thread"></a>So wechseln Sie den aktiven Thread  
  
- Führen Sie einen der folgenden Schritte aus:  
  
  - Doppelklicken Sie auf einen beliebigen Thread.  

  - Klicken Sie mit der rechten Maustaste auf einen Thread und dann **auf zu Thread wechseln**.  

    Der gelbe Pfeil wird neben dem neuen aktiven Thread angezeigt. Die grauen Konturen eines Pfeils geben den Thread, in dem der Debugger die Ausführung unterbrochen hat.  
  
## <a name="grouping-and-sorting-threads"></a>Gruppieren und Sortieren von Threads  
 Beim Gruppieren von Threads wird in der Tabelle eine Überschrift für jede Gruppe angezeigt. Die Überschrift enthält eine Gruppenbeschreibung (z. B. "Arbeitsthread" oder "Nicht gekennzeichnete Threads") und ein Strukturansicht-Steuerelement. Die einzelnen Threads jeder Gruppe werden unter der Gruppenüberschrift angezeigt. Wenn Sie die einzelnen Threads einer Gruppe ausblenden möchten, können Sie die Gruppe mithilfe des Strukturansicht-Steuerelements reduzieren.  
  
 Da die Gruppierung Vorrang gegenüber der Sortierung hat, können Sie Threads z. B. nach Kategorien gruppieren und anschließend in den einzelnen Kategorien nach ID sortieren.  
  
#### <a name="to-sort-threads"></a>So sortieren Sie Threads  
  
1. Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
2. Wenn Sie die Sortierreihenfolge umkehren möchten, klicken Sie erneut auf dieselbe Schaltfläche.  
  
     Threads, die am Anfang der Liste angezeigt wurden, werden nun am Ende der Liste aufgeführt.  
  
#### <a name="to-group-threads"></a>So gruppieren Sie Threads  
  
- Klicken Sie in der Symbolleiste des Fensters **Threads** auf die Liste **Gruppieren nach** , und klicken Sie dann auf die Kriterien, nach denen Sie Threads gruppieren möchten.  
  
#### <a name="to-sort-threads-within-groups"></a>So sortieren Sie Threads innerhalb von Gruppen  
  
1. Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf die Liste **Gruppieren nach** , und klicken Sie dann auf die Kriterien, nach denen Sie Threads gruppieren möchten.  
  
2. Klicken Sie im Fenster **Threads** auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>So erweitern oder reduzieren Sie alle Gruppen  
  
- Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf **Gruppen erweitern** oder **Gruppen**reduzieren.  
  
## <a name="searching-for-specific-threads"></a>Suchen nach bestimmten Threads  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] können Sie nach Threads suchen, die einer bestimmten Zeichenfolge entsprechen. Wenn Sie im Fenster **Threads** nach Threads suchen, werden im Fenster alle Threads angezeigt, die der Such Zeichenfolge in einer beliebigen Spalte entsprechen. Diese Informationen enthalten den Thread Speicherort, der oben in der-aufrufszeile in der Spalte **Speicherort** angezeigt wird. Standardmäßig wird jedoch nicht die vollständige Aufrufliste durchsucht.  
  
#### <a name="to-search-for-specific-threads"></a>So suchen Sie nach bestimmten Threads  
  
- Wechseln Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** in das Feld **Suchen**, und führen Sie Folgendes aus:  
  
  - Geben Sie eine Suchzeichenfolge ein, und drücken Sie dann die EINGABETASTE.  

    \- oder -  

  - Klicken Sie neben dem **Suchfeld** auf die Dropdown Liste, und wählen Sie eine Such Zeichenfolge aus einer vorherigen Suche aus.  
  
- (Optional) Wenn bei der Suche die vollständige Aufrufliste berücksichtigt werden soll, wählen Sie **Aufrufliste durchsuchen** aus.  
  
## <a name="freezing-and-thawing-threads"></a>Sperren und Entsperren von Threads  
 Wenn ein Thread eingefroren ist, wird die Threadausführung vom System auch dann nicht gestartet, wenn Ressourcen verfügbar sind.  
  
 In nativem Code können Sie Threads aussetzen oder fortsetzen, indem Sie die Windows `SuspendThread` -Funktionen und `ResumeThread` oder die MFC-Funktionen [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) und [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5)aufrufen. Wenn Sie `SuspendThread` oder aufruft `ResumeThread` , ändern Sie die *Anzahl*der angehaltenen, die im Fenster **Threads** angezeigt wird. Wenn Sie jedoch einen systemeigenen Thread einfrieren oder reaktivieren, wird dadurch der Unterbrechungszähler nicht geändert. Im systemeigenen Code kann ein Thread nur ausgeführt werden, wenn er reaktiviert ist und sein Unterbrechungszähler den Wert 0 aufweist.  
  
 In verwaltetem Code hat das Einfrieren oder Reaktivieren keinen Einfluss auf den Wert des Unterbrechungszählers. In verwaltetem Code hat ein eingefrorener Thread den Unterbrechungszähler 1 auf. In nativem Code hat der Unterbrechungszähler eines eingefrorenen Threads den Wert 0, es sei denn, seine Ausführung wurde durch einen `SuspendThread`-Aufruf unterbrochen.  
  
> [!NOTE]
> Beim Debuggen eines Aufrufs vom nativen Code in den verwalteten Code wird der verwaltete Code im selben physischen Thread ausgeführt wie der native Code, durch den er aufgerufen wurde. Durch Unterbrechen oder Sperren des systemeigenen Threads wird auch der verwaltete Code gesperrt.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>So können Sie die Ausführung eines Threads einfrieren oder reaktivieren  
  
- Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf **Threads Einfrieren** oder **Threads**durch klicken.  
  
     Dieser Vorgang wirkt sich nur auf Threads aus, die im Fenster **Threads** ausgewählt sind.  
  
## <a name="displaying-flagged-threads"></a>Anzeigen von gekennzeichneten Threads  
 Einen Thread, der besondere Aufmerksamkeit erhalten soll, können Sie kennzeichnen, indem Sie ihn im Fenster **Threads** mit einem Symbol markieren. Weitere Informationen finden Sie unter Gewusst [wie: markieren und](../debugger/how-to-flag-and-unflag-threads.md)Aufheben der Flag von Threads. Im Fenster "Threads" können Sie festlegen, dass alle Threads oder nur die gekennzeichneten Threads angezeigt werden.  
  
#### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
- Wählen Sie in der oberen linken Ecke des Fensters **Threads** die Schaltfläche Flag aus.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Anzeigen von Threadaufruflisten und Wechseln zwischen Rahmen  
 In einem Multithreadprogramm verfügt jeder Thread über eine eigene Aufrufliste. Das Fenster **Threads** bietet eine benutzerfreundliche Möglichkeit, sich diese anzeigen zu lassen.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>So zeigen Sie die Aufrufliste eines Threads an  
  
- Klicken Sie in der Spalte **Speicherort** auf das umgekehrte Dreieck neben dem Thread Speicherort.  
  
     Der Speicherort wird erweitert, und die Aufrufliste für den Thread wird angezeigt.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>So können Sie die Aufruflisten aller Threads anzeigen oder reduzieren  
  
- Klicken Sie in der Symbolleiste am oberen Rand des Fensters **Threads** auf **Aufruf Listen erweitern** oder **Aufruf**Listen reduzieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md)
