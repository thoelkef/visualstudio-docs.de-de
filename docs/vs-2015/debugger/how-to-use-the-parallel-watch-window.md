---
title: 'Vorgehensweise: Verwenden des parallelen Überwachungsfensters | Microsoft-Dokumentation'
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
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5d8354c850d1f55d229ce3f1205ca0bf0fe5f13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837073"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Gewusst wie: Verwenden des parallelen Überwachungsfensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im parallelen Überwachungsfenster können Sie gleichzeitig die Werte anzeigen, die ein Ausdruck auf mehreren Threads enthält. Jede Zeile stellt einen Thread in einer Anwendung ausgeführten dar. Allerdings wird ein Thread möglicherweise in mehreren Zeilen angezeigt werden. Genauer gesagt stellt jede Zeile einen Funktionsaufruf dar, dessen Funktionssignatur der Funktion auf dem aktuellen Stapelrahmen entspricht. Sie können die Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads kennzeichnen bzw. die Kennzeichnung aufheben, ihn einfrieren (anhalten) und reaktivieren (fortsetzen). Die folgenden Spalten werden angezeigt, der **parallele Überwachung** Fenster:  
  
- Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.  
  
- Die Framespalte, in der ein Pfeil den ausgewählten Frame angibt.  
  
- Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.  
  
  > [!TIP]
  >  Müssen Sie öffnen die **parallele Aufgabe** Fenster aus, um die Aufgabeninformationen im Anzeigen der **parallele Überwachung** Fenster.  
  
- Die  **\<Überwachung hinzufügen >** Spalte, in dem Sie Ausdrücke zur Überwachung eingeben können.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>So zeigen Sie das parallele Überwachungsfenster an  
  
1.  Legen Sie einen Haltepunkt im Code fest.  
  
2.  Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.  
  
3.  Wählen Sie auf der Menüleiste **Debuggen**, **Windows**, **parallele Überwachung**, und wählen Sie dann ein Fenster "überwachen". Sie können bis zu vier Fenster öffnen.  
  
### <a name="to-add-a-watch-expression"></a>So fügen Sie einen Überwachungsausdruck hinzu  
  
-   Wählen Sie  **\<Überwachung hinzufügen >** und geben Sie einen Überwachungsausdruck.  
  
### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf  
  
-   Wählen Sie die Spalte zur Kennzeichnung für die Zeile, oder öffnen Sie das Kontextmenü für den Thread aus, und wählen Sie **Flag** oder **Flag**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie die Schaltfläche "nur gekennzeichnete Threads anzeigen" in der oberen linken Ecke des der **parallele Überwachung** Fenster.  
  
### <a name="to-switch-frames"></a>So wechseln Sie Frames  
  
-   Doppelklicken Sie auf die Framespalte. (Tastatur: Wählen Sie die Zeile aus, und drücken Sie EINGABETASTE.)  
  
### <a name="to-sort-a-column"></a>So sortieren Sie eine Spalte  
  
-   Wählen Sie Spaltenüberschrift aus.  
  
### <a name="to-group-threads"></a>So gruppieren Sie Threads  
  
-   Öffnen Sie das Kontextmenü für das parallele Überwachungsfenster, wählen **Group By**, und wählen Sie dann das entsprechende Untermenüelement.  
  
### <a name="to-freeze-or-thaw-threads"></a>So frieren Sie Threads ein oder reaktivieren sie  
  
-   Öffnen Sie das Kontextmenü für die Zeile, und wählen **fixieren** oder **reaktivieren**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>So exportieren Sie Daten in das parallele Überwachungsfenster  
  
-   Wählen Sie die **in Excel öffnen** Schaltfläche, und wählen Sie dann **in Excel öffnen** oder **exportieren nach CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>So filtern Sie nach einem booleschen Ausdruck  
  
-   Geben Sie einen booleschen Ausdruck in der **nach booleschem Ausdruck filtern** Feld. Vom Debugger wird der Ausdruck für jeden Threadkontext ausgewertet. Nur Zeilen mit einem Wert von `true` werden angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Vorgehensweise: Verwenden Sie das GPU-Threadfenster](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



