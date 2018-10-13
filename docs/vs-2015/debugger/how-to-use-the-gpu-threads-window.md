---
title: 'Vorgehensweise: Verwenden Sie das GPU-Threadfenster | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c58bed9dd25cc9d25ad122b4c4c42f72ddf60f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236807"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Gewusst wie: Verwenden des Fensters "GPU-Threads"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Fenster "GPU-Threads" können Sie Threads in der debuggten GPU überprüfen und diese bearbeiten. Weitere Informationen zu Anwendungen, die auf dem GPU ausgeführt werden, finden Sie unter [Übersicht über C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 Das GPU-Threadfenster enthält eine Tabelle, in der jede Zeile einen Satz GPU-Threads darstellt, die in allen Spalten über die gleichen Werte verfügen. Sie können Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads aus dem GPU-Threadfenster heraus kennzeichnen, die Kennzeichnung aufheben, sie einfrieren (anhalten), und reaktivieren (fortsetzen). Die folgenden Spalten werden im GPU-Threadfenster angezeigt:  
  
-   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.  
  
-   Die Spalte mit aktiven Threads, in der ein gelber Pfeil einen aktiven Thread anzeigt. Ein Pfeil gibt den Thread an, in dem die Ausführung durch den Debugger unterbrochen wurde.  
  
-   Die **Threadanzahl** Spalte, die die Anzahl der Threads an derselben Position anzeigt.  
  
-   Die **Zeile** Spalte, die die Zeile des Codes angezeigt wird, in dem jede Gruppe von Threads befindet.  
  
-   Die **Adresse** Spalte, in der die Anweisungsadresse angezeigt wird, in dem jede Gruppe von Threads befindet. Standardmäßig ist diese Spalte ausgeblendet.  
  
-   Die **Speicherort** Spalte, die die Position in der Quellcode ist.  
  
-   Die **Status** Spalte, die anzeigt, ob der Thread aktiv, blockiert, nicht gestartet oder abgeschlossen ist.  
  
-   Die **Kachel** Spalte, in der der kachelindex für die Threads in der Zeile anzeigt.  
  
 Im Header der Tabelle werden die Kachel und der Thread, die dargestellt werden, angezeigt.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>So öffnen Sie das GPU-Threadfenster  
  
1.  Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.  
  
2.  In der **Eigenschaftenseiten** Fenster für das Projekt unter **Konfigurationseigenschaften**, wählen Sie **Debuggen**.  
  
3.  In der **zu startender Debugger** Liste **lokaler Windows-Debugger**. In der **Debuggertyp** Liste **nur GPU**. Sie müssen für diesen Debugger festlegen, im Code, der auf der GPU ausgeführt wird, am Haltepunkt zu unterbrechen.  
  
4.  Klicken Sie auf die Schaltfläche **OK** .  
  
5.  Legen Sie einen Haltepunkt im GPU-Code fest.  
  
6.  Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.  
  
7.  Eine Menüleiste den Menüpunkt wählen **Debuggen**, **Windows**, **GPU-Threads**.  
  
### <a name="to-change-to-a-different-active-thread"></a>So wechseln Sie zu einem anderen aktiven Thread  
  
-   Doppelklicken Sie auf die Spalte. (Tastatur: Wählen Sie die Zeile aus, und drücken Sie die EINGABETASTE.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>So zeigen Sie eine bestimmte Kachel und einen bestimmten Thread an  
  
1.  Wählen Sie die **Threadumschaltung erweitern** GPU-Threadfenster die Schaltfläche.  
  
2.  Geben Sie die Kachel- und Threadwerte in den Textfeldern an.  
  
3.  Wählen Sie die Schaltfläche mit dem Pfeil darauf aus.  
  
### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus  
  
-   Öffnen Sie das Kontextmenü für das GPU-Threadfenster, und wählen **Spalten**, und wählen Sie dann auf die Spalte, die Sie anzeigen oder ausblenden möchten.  
  
### <a name="to-sort-by-a-column"></a>So sortieren Sie nach Spalte  
  
-   Wählen Sie Spaltenüberschrift aus.  
  
### <a name="to-group-threads"></a>So gruppieren Sie Threads  
  
-   Öffnen Sie das Kontextmenü für das GPU-Threadfenster, und wählen **Group By**, und wählen Sie dann eine der angezeigten Spaltennamen. Wählen Sie **keine** auf die Gruppierung der Threads aufzuheben.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>So können Sie eine Threadzeile einfrieren oder reaktivieren  
  
-   Öffnen Sie das Kontextmenü für die Zeile, und wählen **fixieren** oder **reaktivieren**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>So können Sie Threadzeile kennzeichnen oder die Kennzeichnung aufheben  
  
-   Wählen Sie die Spalte zur Kennzeichnung für den Thread, oder öffnen Sie das Kontextmenü für den Thread aus, und wählen Sie **Flag** oder **Flag**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie im GPU-Threadfenster die Schaltfläche "Kennzeichnen" aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Vorgehensweise: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



