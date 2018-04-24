---
title: Anzeigen von Threads im Debugger | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec5cdf340002c9f454c67b170b4e849360de0166
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Anzeigen von Threads im Debugger in Visual Studio mithilfe des Fensters Threads
In der **Threads** Fenster, die Sie untersuchen und Arbeiten mit Threads in der Anwendung, die Sie debuggen können. Schrittweise Anleitung für die Verwendung der **Threads** Fenster finden Sie unter [Exemplarische Vorgehensweise: Debuggen über das Fenster "Threads"](../debugger/how-to-use-the-threads-window.md).
  
 Die **Threads** Fenster enthält eine Tabelle, in dem jede Zeile stellt einen Thread in der Anwendung dar. Standardmäßig sind in der Tabelle alle Threads in der Anwendung aufgeführt. Sie können die Liste jedoch filtern, sodass nur die gewünschten Threads angezeigt werden. Jede Spalte enthält einen anderen Typ von Informationen. Sie können auch einige Spalten ausblenden. Wenn alle Spalten eingeblendet sind, werden die folgenden Informationen angezeigt (von links nach rechts):  
  
-   Die Flagspalte, in Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll. Informationen dazu, wie Sie einen Thread kennzeichnen, finden Sie unter [Vorgehensweise: Flag und Aufheben der Kennzeichnung von Threads](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Der aktuelle Thread-Spalte, die in der ein gelber Pfeil gibt den aktuellen Thread an (Konturen Pfeil gibt den aktuellen Kontext des Debuggers für eine nicht-aktuellen Threads).
  
-   Die **ID** Spalte, die die ID für jeden Thread enthält.  
  
-   Die **verwaltete ID** Spalte, die die verwalteten IDs für verwaltete Threads enthält.  
  
-   Die **Kategorie** Spalte, die Threads als Benutzeroberflächenthreads, Remoteprozeduraufruf-Handler oder Arbeitsthreads kategorisiert werden. In einer speziellen Kategorie wird der Hauptthread der Anwendung angegeben.  
  
-   Die **Namen** Spalte, in der jeder Thread anhand des Namens, zu identifizieren, sofern vorhanden, oder als \<ohne Namen >.  
  
-   Die **Speicherort** Spalte, der angezeigt wird, in dem der Thread ausgeführt wird. Sie können diesen Speicherort erweitern, um die vollständige Aufrufliste für den Thread anzuzeigen.  
  
-   Die **Priorität** Spalte, die die Priorität bzw. Rangfolge, die jeder Thread der vom System zugewiesen wurde.  
  
-   Die **Affinity Mask** Spalte, die eine erweiterte Spalte (in der Regel ausgeblendet) ist. In dieser Spalte wird die Prozessor-Affinitätsmaske für jeden Thread angezeigt. In einem Multiprozessorsystem bestimmt die Affinitätsmaske die Prozessoren, auf denen ein Thread ausgeführt werden kann.  
  
-   Die **angehaltene Anzahl** Spalte (in der Regel ausgeblendet), enthält den Unterbrechungszähler angegeben, und ist normalerweise verborgen. Dieser Zähler bestimmt, ob ein Thread ausgeführt werden kann. Eine Erläuterung des Unterbrechungszählers finden Sie in diesem Thema im Abschnitt "Sperren und Entsperren von Threads".  
  
-   Die **Prozessnamen** Spalte (in der Regel ausgeblendet), die den Prozess aufführt, zu der jeder Thread gehört. Diese Spalte kann nützlich sein, wenn Sie mehrere Prozesse debuggen.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>So zeigen Sie das Fenster Threads im Unterbrechungs- oder Ausführmodus an  
  
-   Wählen Sie während des Debuggens die **Debuggen** Sie im Menü **Windows**, und klicken Sie dann auf **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf **Spalten**, und aktivieren bzw. deaktivieren Sie den Namen der Spalte, die Sie anzeigen oder ausblenden möchten.    

## <a name="display-flagged-threads"></a>Gekennzeichnete Threads anzeigen  
 Kennzeichnen Sie einen Thread, der besondere Aufmerksamkeit erhalten, markieren Sie es mit einem Symbol in der **Threads** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Flag und Aufheben der Kennzeichnung von Threads](../debugger/how-to-flag-and-unflag-threads.md). In der **Threads** Fenster können auf alle Threads oder nur gekennzeichnete Threads anzeigen.  
  
#### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie die **nur gekennzeichnete Threads anzeigen Threads** Schaltfläche am oberen Rand der **Threads** Fenster. (Wenn es abgeblendet ist, müssen Sie zunächst einige Threads kennzeichnen.) 

## <a name="freeze-and-thaw-threads"></a>Einfrieren und Reaktivieren von Threads  
 Wenn ein Thread eingefroren ist, wird die Threadausführung vom System auch dann nicht gestartet, wenn Ressourcen verfügbar sind.  
  
 In systemeigenem Code können Sie anhalten oder Fortsetzen von Threads durch Aufruf der Windows-Funktionen `SuspendThread` und `ResumeThread` oder die MFC-Funktionen [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__suspendthread) und [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__resumethread). Beim Aufrufen `SuspendThread` oder `ResumeThread`, Sie ändern die *Unterbrechungszähler*, das angezeigt wird, der **Threads** Fenster. Wenn Sie jedoch einen systemeigenen Thread einfrieren oder reaktivieren, wird dadurch der Unterbrechungszähler nicht geändert. Im systemeigenen Code kann ein Thread nur ausgeführt werden, wenn er reaktiviert ist und sein Unterbrechungszähler den Wert 0 aufweist.  
  
 In verwaltetem Code hat das Einfrieren oder Reaktivieren keinen Einfluss auf den Wert des Unterbrechungszählers. In verwaltetem Code hat ein eingefrorener Thread den Unterbrechungszähler 1 auf. In systemeigenem Code hat der Unterbrechungszähler eines eingefrorenen Threads den Wert 0, es sei denn, seine Ausführung wurde durch einen `SuspendThread`-Aufruf unterbrochen.  
  
> [!NOTE]
>  Beim Debuggen eines Aufrufs vom systemeigenen Code in den verwalteten Code wird der verwaltete Code im selben physischen Thread ausgeführt wie der systemeigene Code, durch den er aufgerufen wurde. Durch Unterbrechen oder Sperren des systemeigenen Threads wird auch der verwaltete Code gesperrt.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>So können Sie die Ausführung eines Threads einfrieren oder reaktivieren  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf **Threads einfrieren** oder **Threads reaktivieren**.  
  
     Dieser Vorgang wirkt sich nur auf Threads aus, die im ausgewählten der **Threads** Fenster. 

### <a name="switch-to-another-thread"></a>Wechseln Sie zu einem anderen thread 

Ein gelber Pfeil gibt den aktuellen Thread (und die Position des Zeigers Ausführung). Ein grüner Pfeil in Form einer Welle gibt an, dass ein nicht-aktuellen Thread der aktuelle Kontext des Debuggers verfügt.

#### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen thread  
  
-   Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf einen beliebigen Thread.  
  
    -   Mit der rechten Maustaste eines Threads, und klicken Sie auf **zu Thread wechseln**.

## <a name="group-and-sort-threads"></a>Gruppieren und Sortieren von Threads  
 Beim Gruppieren von Threads wird in der Tabelle eine Überschrift für jede Gruppe angezeigt. Die Überschrift enthält eine Gruppenbeschreibung (z. B. "Arbeitsthread" oder "Nicht gekennzeichnete Threads") und ein Strukturansicht-Steuerelement. Die einzelnen Threads jeder Gruppe werden unter der Gruppenüberschrift angezeigt. Wenn Sie die einzelnen Threads einer Gruppe ausblenden möchten, können Sie die Gruppe mithilfe des Strukturansicht-Steuerelements reduzieren.  
  
 Da die Gruppierung Vorrang gegenüber der Sortierung hat, können Sie Threads z. B. nach Kategorien gruppieren und anschließend in den einzelnen Kategorien nach ID sortieren.  
  
#### <a name="to-sort-threads"></a>So sortieren Sie Threads  
  
1.  Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
2.  Wenn Sie die Sortierreihenfolge umkehren möchten, klicken Sie erneut auf dieselbe Schaltfläche.  
  
     Threads, die am Anfang der Liste angezeigt wurden, werden nun am Ende der Liste aufgeführt.  
  
#### <a name="to-group-threads"></a>So gruppieren Sie Threads  
  
-   In der **Threads** Symbolleiste des Fensters klicken Sie auf die **Gruppieren nach** und dann auf die Kriterien, die Sie Threads gruppieren möchten.  
  
#### <a name="to-sort-threads-within-groups"></a>So sortieren Sie Threads innerhalb von Gruppen  
  
1.  Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf die **Gruppieren nach** und dann auf die Kriterien, die Sie Threads gruppieren möchten.  
  
2.  In der **Threads** Fenster, klicken Sie auf die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>So erweitern oder reduzieren Sie alle Gruppen  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf **Gruppen erweitern** oder **Gruppen reduzieren**.  
  
## <a name="search-for-specific-threads"></a>Suchen Sie nach bestimmten Threads  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie nach Threads suchen, die einer bestimmten Zeichenfolge entsprechen. Bei der Suche nach Threads in der **Threads** , im Fenster werden alle Threads angezeigt, die mit die Suchzeichenfolge in einer beliebigen Spalte übereinstimmen. Dass Informationen zählt der Threadspeicherort, der am oberen Rand der Aufrufliste in der **Speicherort** Spalte. Standardmäßig wird jedoch nicht die vollständige Aufrufliste durchsucht.  
  
#### <a name="to-search-for-specific-threads"></a>So suchen Sie nach bestimmten Threads  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** Fenster, wechseln Sie zu der **Suche** Feld, und:  
  
    -   Geben Sie eine Suchzeichenfolge ein, und drücken Sie dann die EINGABETASTE.  
  
         \- oder –  
  
    -   Klicken Sie auf die Dropdownliste neben der **Suche** Feld, und wählen Sie eine Suchzeichenfolge aus einem früheren Suchvorgang.  
  
-   (Optional) Um die vollständige Aufrufliste in die Suche einbeziehen möchten, wählen Sie **Aufrufliste suchen**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Anzeigen von Threadaufruflisten und Wechseln zwischen Rahmen  
In einem Multithreadprogramm verfügt jeder Thread über eine eigene Aufrufliste. Die **Threads** Fenster stellt eine einfache Möglichkeit, diese Aufruflisten anzuzeigen.

> [!TIP]
> Verwenden Sie für eine visuelle Darstellung der Aufrufliste für jeden Thread, der [parallele Stapel](../debugger/get-started-debugging-multithreaded-apps.md) Fenster.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>So zeigen Sie die Aufrufliste eines Threads an  
  
-   In der **Speicherort** Spalte, klicken Sie auf das umgekehrte Dreieck neben dem Threadspeicherort.  
  
     Der Speicherort wird erweitert, und die Aufrufliste für den Thread wird angezeigt.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>So können Sie die Aufruflisten aller Threads anzeigen oder reduzieren  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf **Aufruflisten erweitern** oder **Aufruflisten reduzieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Erste Schritte zum Debuggen einer Multithreadanwendung](../debugger/get-started-debugging-multithreaded-apps.md)