---
title: 'Vorgehensweise: kennzeichnen und Kennzeichnung von Threads | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 489403e4ce5052cb526a361e4548ab8823a20b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flag-and-unflag-threads"></a>Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung
Kennzeichnen Sie einen Thread, der besondere Aufmerksamkeit erhalten, markieren Sie es mit einem Symbol in der **Threads**, **parallele Stapel** (thread anzeigen), **parallele Überwachung**, und  **GPU-Threads** Windows. Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
Gekennzeichnete Threads werden auch in eine besondere Behandlung der **Thread** auf in der Liste der **Debugspeicherort** Symbolleiste und in den anderen Multithread Debugfenstern. Sie können alle Threads oder nur gekennzeichnete Threads Anzeigen der **Thread** Liste oder in den anderen Fenstern.
  
### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf 
  
-   In der **Threads** oder **parallele Überwachung** Fenster, suchen Sie den Thread, der Sie interessiert sind, und klicken Sie auf das Kennzeichnungssymbol aktivieren oder deaktivieren das Flag. 
-   In der **parallele Stapel** mit der rechten Maustaste auf einen Thread oder eine Gruppe von Threads und wählen Sie im Fenster **Flag / <thread>**  oder **Flag entfernen / <thread>** .
  
### <a name="to-unflag-all-threads"></a>So heben Sie die Kennzeichnung aller Threads auf  
  
-   In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **Kennzeichnung aller Threads**.
-   In der **parallele Überwachung** wählen alle gekennzeichnete Threads an, mit der rechten Maustaste, und wählen Sie **Flag**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie die **nur gekennzeichnete Threads anzeigen Threads** Schaltfläche in einem Multithread-debugging-Fenster.  
  
### <a name="to-flag-just-my-code"></a>So kennzeichnen Sie nur eigenen Code  
  
1.  Auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **nur eigenen Code kennzeichnen**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>So kennzeichnen Sie Threads, die ausgewählten Modulen zugeordnet sind  
  
1.  Auf der Symbolleiste der **Threads** Fenster, klicken Sie auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **benutzerdefinierte Modulauswahl kennzeichnen**.  
  
3.  In der **Module auswählen** Dialogfeld wählen die gewünschten Module.  
  
4.  (Optional) In der **Suche** geben eine Zeichenfolge, die für bestimmte Module zu suchen.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Erste Schritte zum Debuggen von Multithreadanwendungen verwendet werden können](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Exemplarische Vorgehensweise: Debuggen von Multithreadanwendungen mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md)