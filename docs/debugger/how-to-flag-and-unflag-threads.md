---
title: 'Vorgehensweise: Kennzeichnen und Kennzeichnung von Threads | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52103870207ae93731cc82969abdd377aff2d381
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851403"
---
# <a name="how-to-flag-and-unflag-threads"></a>Vorgehensweise: Kennzeichnen von Threads und Aufheben der Kennzeichnung
Sie können einen Thread, der besondere Aufmerksamkeit erhalten, indem Sie es mit einem Symbol im markieren möchten kennzeichnen die **Threads**, **parallele Stapel** (thread anzeigen), **parallele Überwachung**, und  **GPU-Threads** Windows. Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
Gekennzeichnete Threads werden auch in eine besondere Behandlung der **Thread** auf in der Liste der **Debugspeicherort** Symbolleiste und in die andere Multithread debugging-Fenster. Sie können anzeigen, alle Threads oder nur gekennzeichnete Threads in der **Thread** Liste oder in den anderen Fenstern.
  
### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf 
  
- In der **Threads** oder **parallele Überwachung** Fenster Suchen Sie den Thread, der Sie interessiert sind, und klicken Sie auf das Flaggensymbol klicken, aktivieren oder deaktivieren das Flag. 
- In der **parallele Stapel** , mit der rechten Maustaste auf einen Thread oder eine Gruppe von Threads, und wählen Sie im Fenster **Flag / <thread>**  oder **Flag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>So heben Sie die Kennzeichnung aller Threads auf  
  
-   Klicken Sie im Fenster **Threads** mit der rechten Maustaste auf einen Thread, und klicken Sie anschließend auf **Kennzeichnung aller Threads aufheben**.
-   In der **parallele Überwachung** wählen Sie im Fenster alle gekennzeichnete Threads, mit der rechten Maustaste, und wählen Sie **Flag**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie die **nur gekennzeichnete Threads anzeigen Threads** Schaltfläche in einem der die Multithread-debugging-Fenster.  
  
### <a name="to-flag-just-my-code"></a>So kennzeichnen Sie nur eigenen Code  
  
1.  Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **Nur eigenen Code kennzeichnen**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>So kennzeichnen Sie Threads, die ausgewählten Modulen zugeordnet sind  
  
1.  Klicken Sie auf der Symbolleiste des Fensters **Threads** auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **Benutzerdefinierte Modulauswahl kennzeichnen**.  
  
3.  Wählen Sie im Dialogfeld **Module auswählen** die gewünschten Module aus.  
  
4.  (Optional) Geben Sie Im Feld **Suchen** eine Suchzeichenfolge für bestimmte Module ein.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von Multithreadanwendungen in Visual Studio](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Exemplarische Vorgehensweise: Debuggen von Multithreadanwendungen, die mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md)