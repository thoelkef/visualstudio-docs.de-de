---
title: 'Vorgehensweise: kennzeichnen und Kennzeichnung von Threads | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 09d26c87867e071b7dafce80d95e4bc46cb88bb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891374"
---
# <a name="how-to-flag-and-unflag-threads"></a>Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung
Sie können einen Thread, der besondere Aufmerksamkeit erhalten, indem Sie es mit einem Symbol im markieren möchten kennzeichnen die **Threads**, **parallele Stapel** (thread anzeigen), **parallele Überwachung**, und  **GPU-Threads** Windows. Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
Gekennzeichnete Threads werden auch in eine besondere Behandlung der **Thread** auf in der Liste der **Debugspeicherort** Symbolleiste und in die andere Multithread debugging-Fenster. Sie können anzeigen, alle Threads oder nur gekennzeichnete Threads in der **Thread** Liste oder in den anderen Fenstern.
  
### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf 
  
- In der **Threads** oder **parallele Überwachung** Fenster Suchen Sie den Thread, der Sie interessiert sind, und klicken Sie auf das Flaggensymbol klicken, aktivieren oder deaktivieren das Flag. 
- In der **parallele Stapel** , mit der rechten Maustaste auf einen Thread oder eine Gruppe von Threads, und wählen Sie im Fenster **Flag / <thread>**  oder **Flag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>So heben Sie die Kennzeichnung aller Threads auf  
  
-   In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **Kennzeichnung aller Threads**.
-   In der **parallele Überwachung** wählen Sie im Fenster alle gekennzeichnete Threads, mit der rechten Maustaste, und wählen Sie **Flag**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie die **nur gekennzeichnete Threads anzeigen Threads** Schaltfläche in einem der die Multithread-debugging-Fenster.  
  
### <a name="to-flag-just-my-code"></a>So kennzeichnen Sie nur eigenen Code  
  
1.  Klicken Sie auf der Symbolleiste am oberen Rand der **Threads** Fenster, klicken Sie auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **nur eigenen Code kennzeichnen**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>So kennzeichnen Sie Threads, die ausgewählten Modulen zugeordnet sind  
  
1.  Auf der Symbolleiste des der **Threads** Fenster, klicken Sie auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **benutzerdefinierte Modulauswahl kennzeichnen**.  
  
3.  In der **Module auswählen** Dialogfeld wählen die Module, die Sie möchten.  
  
4.  (Optional) In der **Suche** geben eine Zeichenfolge, die für bestimmte Module zu suchen.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Exemplarische Vorgehensweise: Debuggen von Multithreadanwendungen, die mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md)