---
title: Anzeigen von Threads im Debugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/29/2018
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
ms.openlocfilehash: 14b170e6f8259776941ce0fcc2a2866a9084cffb
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607717"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window"></a>Threads in Visual Studio-Debugger mithilfe des Fensters Threads anzeigen
In der **Threads** Fenster, die Sie untersuchen und Arbeiten mit Threads in der Anwendung, die Sie debuggen können. Schrittweise Anleitung zur Verwendung der **Threads** Fenster finden Sie unter [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Verwenden des Fensters „Threads“ 
 Die **Threads** Fenster enthält eine Tabelle, in dem jede Zeile einen separaten Thread in der Anwendung beschreibt. In der Standardeinstellung die Tabelle enthält alle Threads in Ihrer Anwendung, aber Sie können die Liste, um nur die Threads anzeigen, die Sie interessieren filtern. Jede Spalte wird eine andere Art von Informationen beschrieben. Sie können auch einige Spalten ausblenden. Wenn Sie alle Spalten anzeigen, werden die folgenden Spalten von links nach rechts angezeigt:  
  
- **Flag**: In diesem Artikel noch nicht gekennzeichneten können Sie markieren einen Thread, besondere Aufmerksamkeit werden soll. Weitere Informationen zum Kennzeichnen von Threads, finden Sie unter [Vorgehensweise: Flag und Aufheben der Kennzeichnung Threads](../debugger/how-to-flag-and-unflag-threads.md).  
  
- **Aktuellen Thread**: In diesem Artikel noch nicht gekennzeichneten ein gelber Pfeil gibt den aktuellen Thread. Eine Gliederung Pfeil gibt den aktuellen Debuggerkontext für eine nicht-aktuellen Threads an.
  
- **ID**: die ID für jeden Thread angezeigt.  
  
- **Verwaltete ID**: Zeigt die verwalteten IDs für verwaltete Threads.  
  
- **Kategorie**: Zeigt die Kategorie der Threads als Benutzeroberflächenthreads, Remoteprozeduraufruf-Handler oder Arbeitsthreads. In einer speziellen Kategorie wird der Hauptthread der Anwendung angegeben.  
  
- **Namen**: identifiziert jeden Thread den Namen, sofern vorhanden, oder als \<ohne Namen >.  
  
- **Speicherort**: Zeigt, in dem der Thread ausgeführt wird. Sie können diesen Speicherort erweitern, um die vollständige Aufrufliste für den Thread anzuzeigen.  
  
- **Priorität**: eine erweiterte Spalte (standardmäßig ausgeblendet), die anzeigt, die Priorität bzw. Rangfolge, die das System für jeden Thread zugewiesen wurden.  
  
- **Affinitätsmaske**: eine erweiterte Spalte (standardmäßig ausgeblendet), die der Prozessor-Affinitätsmaske für jeden Thread anzeigt. In einem Multiprozessorsystem bestimmt die Affinitätsmaske die Prozessoren, auf denen ein Thread ausgeführt werden kann.  
  
- **Unterbrechungszähler**: eine erweiterte Spalte (standardmäßig ausgeblendet), die die Anzahl die angehaltene anzeigt. Dieser Zähler bestimmt, ob ein Thread ausgeführt werden kann. Weitere Informationen zu der Anzahl der angehaltenen, finden Sie unter [Einfrieren und Reaktivieren von Threads](#freeze-and-thaw-threads).  
  
- **Prozessname**: eine erweiterte Spalte (standardmäßig ausgeblendet), in dem den Prozess angezeigt, zu der jeder Thread gehört. Die Daten in dieser Spalte können nützlich sein, wenn Sie viele Prozesse debuggen.  

- **Prozess-ID**: eine erweiterte Spalte (standardmäßig ausgeblendet), die der Prozess zeigt die ID, zu der jeder Thread gehört. 

- **Transportqualifizierer**: eine erweiterte Spalte (standardmäßig ausgeblendet), die den Computer eindeutig mit dem der Debugger verbunden ist. 
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>So zeigen Sie das Fenster Threads im Unterbrechungs- oder Ausführmodus an  
  
-   Wählen Sie während der Visual Studio im Debugmodus befindet, die **Debuggen** Startmenü **Windows**, und wählen Sie dann **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** wählen Sie im Fenster **Spalten**. Klicken Sie dann aktivieren Sie, oder deaktivieren Sie den Namen der Spalte, die Sie anzeigen oder ausblenden möchten.  

## <a name="display-flagged-threads"></a>Gekennzeichnete Threads anzeigen  
 Sie können einen Thread, der besondere Aufmerksamkeit erhalten, indem Sie es mit einem Symbol im markieren möchten kennzeichnen die **Threads** Fenster. Weitere Informationen finden Sie unter [wie: kennzeichnen und Threadkennzeichnung](../debugger/how-to-flag-and-unflag-threads.md). In der **Threads** Fenster können Sie alle Threads oder nur die gekennzeichneten Threads angezeigt.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie **nur gekennzeichnete Threads anzeigen Threads** auf der Symbolleiste am oberen Rand der **Threads** Fenster. (Wenn es abgeblendet ist, müssen Sie so kennzeichnen Sie zunächst einige Threads). 

## <a name="freeze-and-thaw-threads"></a>Sperren und Threads reaktivieren  
 Wenn Sie einen Thread einfrieren, startet das System Ausführung des Threads nicht, wenn Ressourcen verfügbar sind.  
  
 In nativem Code können Sie anhalten oder Fortsetzen von Threads durch Aufruf der Windows-Funktionen `SuspendThread` und `ResumeThread`. Oder rufen Sie die MFC-Funktionen [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) und [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Aufrufen `SuspendThread` oder `ResumeThread`, *Unterbrechungszähler* angezeigt, der **Threads** Fenster wird geändert. Der Unterbrechungszähler nicht geändert werden, wenn Sie einfrieren oder reaktivieren einen nativen Thread. Ein Thread kann nicht in nativem Code ausführen, es sei denn, er entsperrt ist und 0 (null) aufweist.  
  
 In verwaltetem Code ändert der Unterbrechungszähler angegeben, wenn Sie einfrieren oder ein Threads reaktivieren. Wenn ein Thread in verwaltetem Code eingefroren ist, ist dessen Unterbrechungszähler 1 auf. Fixieren Sie einen Thread in systemeigenem Code, ist dessen Unterbrechungszähler 0 (null), es sei denn, Sie verwendet die `SuspendThread` aufrufen.  
  
> [!NOTE]
>  Beim Debuggen eines Aufrufs vom nativen Code in den verwalteten Code wird der verwaltete Code im selben physischen Thread ausgeführt wie der native Code, durch den er aufgerufen wurde. Durch Unterbrechen oder Sperren des systemeigenen Threads wird auch der verwaltete Code gesperrt.  
  
### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>So können Sie die Ausführung eines Threads einfrieren oder reaktivieren  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** wählen Sie im Fenster **Threads einfrieren** oder **Threads reaktivieren**.  
  
     Dieser Vorgang wirkt sich nur die Threads, die im ausgewählten der **Threads** Fenster. 

### <a name="switch-to-another-thread"></a>Wechseln Sie zu einem anderen thread 

Ein gelber Pfeil gibt den aktuellen Thread (und den Speicherort der Ausführungszeiger) an. Ein grüner Pfeil in Form einer Welle gibt an, dass eine nicht-aktuellen Threads den aktuellen Debuggerkontext hat.

#### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen thread  
  
-   Führen Sie entweder die folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf einen beliebigen Thread.  
  
    -   Mit der rechten Maustaste in eines Threads aus, und wählen Sie **Switch zum Thread**.

## <a name="group-and-sort-threads"></a>Gruppieren und Sortieren von threads  
 Beim Gruppieren von Threads wird in der Tabelle eine Überschrift für jede Gruppe angezeigt. Die Überschrift enthält die Beschreibung einer Gruppe, z. B. **Arbeitsthread** oder **nicht gekennzeichnete Threads**, und ein Strukturansicht-Steuerelement. Die einzelnen Threads jeder Gruppe werden unter der Gruppenüberschrift angezeigt. Wenn Sie die einzelnen Threads einer Gruppe ausblenden möchten, verwenden Sie das Strukturansicht-Steuerelement, um die Gruppe zu reduzieren.  
  
 Da die Gruppierung Vorrang gegenüber der Sortierung hat, können Sie Threads z. B. nach Kategorien gruppieren und anschließend in den einzelnen Kategorien nach ID sortieren.  
  
### <a name="to-sort-threads"></a>So sortieren Sie Threads  
  
1.  Auf der Symbolleiste am oberen Rand der **Threads** Fenster, wählen Sie die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
2.  Wenn Sie die Sortierreihenfolge umkehren möchten, wählen Sie die gleiche Schaltfläche erneut.  
  
     Threads, die am Anfang der Liste angezeigt wurden, werden nun am Ende der Liste aufgeführt.  
  
### <a name="to-group-threads"></a>So gruppieren Sie Threads  
  
-   In der **Threads** Symbolleiste des Fensters auf die **Group by-** Liste, und wählen Sie die Kriterien, die Sie Threads gruppieren möchten.  
  
### <a name="to-sort-threads-within-groups"></a>So sortieren Sie Threads innerhalb von Gruppen  
  
1.  Auf der Symbolleiste am oberen Rand der **Threads** wählen Sie im Fenster der **Group by-** Liste, und wählen Sie die Kriterien, die Sie Threads gruppieren möchten.  
  
2.  In der **Threads** Fenster, wählen Sie die Schaltfläche am oberen Rand einer beliebigen Spalte.  
  
     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.  
  
### <a name="to-expand-or-collapse-all-groups"></a>So erweitern oder reduzieren Sie alle Gruppen  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** wählen Sie im Fenster **Gruppen erweitern** oder **Gruppen reduzieren**.  
  
## <a name="search-for-specific-threads"></a>Suchen Sie nach bestimmten threads  
 Sie können Threads, die in einer bestimmten Zeichenfolge entsprechen Suchen der **Threads** Fenster. Wenn Sie nach Threads suchen, zeigt das Fenster die Threads, die für die Übereinstimmung der Suchzeichenfolge in einer beliebigen Spalte. Diese Informationen zählt der Threadspeicherort, der am oberen Rand der Aufrufliste in angezeigt wird. die **Speicherort** Spalte. Standardmäßig ist nicht die vollständige Aufrufliste durchsucht.  
  
### <a name="to-search-for-specific-threads"></a>So suchen Sie nach bestimmten Threads  
  
1. Auf der Symbolleiste am oberen Rand der **Threads** Fenster, wechseln Sie zu der **Suche** Feld, und:  

     - Geben Sie eine Suchzeichenfolge ein, und drücken Sie dann die **EINGABETASTE**.  
  
     \- oder –  
  
     - Wählen Sie die Dropdownliste neben der **Suche** Feld, und wählen Sie eine Suchzeichenfolge aus einer vorherigen Suche.  
  
2. (Optional) Um die vollständige Aufrufliste in die Suche einbeziehen möchten, wählen Sie **Aufrufliste suchen**.   
  
## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Anzeigen von Threadaufruflisten und wechseln Sie zwischen den frames  
In einem Multithreadprogramm verfügt jeder Thread über eine eigene Aufrufliste. Die **Threads** Fenster bietet eine bequeme Möglichkeit, diese Aufruflisten anzuzeigen.

> [!TIP]
> Verwenden Sie für eine visuelle Darstellung der Aufrufliste für jeden Thread, der [parallele Stapel](../debugger/get-started-debugging-multithreaded-apps.md) Fenster.
  
### <a name="to-view-the-call-stack-of-a-thread"></a>So zeigen Sie die Aufrufliste eines Threads an  
  
-   In der **Speicherort** Spalte wählen Sie das umgekehrte Dreieck neben dem Threadspeicherort.  
  
     Der Speicherort wird erweitert, und die Aufrufliste für den Thread wird angezeigt.  
  
### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>So können Sie die Aufruflisten aller Threads anzeigen oder reduzieren  
  
-   Auf der Symbolleiste am oberen Rand der **Threads** wählen Sie im Fenster **Aufruflisten erweitern** oder **Aufruflisten reduzieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md)