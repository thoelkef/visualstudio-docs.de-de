---
title: 'Vorgehensweise: Kennzeichnen und Kennzeichnung von Threads | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be6ebe9e2031b24442f368b626d53b15a043023c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946501"
---
# <a name="how-to-flag-and-unflag-threads"></a>Vorgehensweise: Kennzeichnen von Threads und Aufheben der Kennzeichnung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einen Thread, der besondere Aufmerksamkeit erhalten, indem Sie es mit einem Symbol im markieren möchten kennzeichnen die **Threads**, **parallele Stapel**, **parallele Überwachung**, und **GPU Threads** Windows. Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
 Gekennzeichnete Threads werden auch in eine besondere Behandlung der **Thread** auf in der Liste der **Debugspeicherort** Symbolleiste. In dieser Liste können alle Threads oder nur gekennzeichnete Threads aufgeführt werden. Wenn Sie einen Thread kennzeichnen die **Thread** Liste wechselt automatisch zum nur gekennzeichnete Threads anzeigen, aber Sie können es wechseln zurück, um alle Threads nach Bedarf anzuzeigen.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>So können Sie einen Thread mithilfe des Fensters Threads kennzeichnen oder seine Kennzeichnung aufheben  
  
-   In der **Threads** Fenster Suchen Sie den Thread, der Sie interessiert sind, und klicken Sie auf das Flaggensymbol klicken, aktivieren oder deaktivieren das Flag.  
  
### <a name="to-unflag-all-threads"></a>So heben Sie die Kennzeichnung aller Threads auf  
  
-   Klicken Sie im Fenster **Threads** mit der rechten Maustaste auf einen Thread, und klicken Sie anschließend auf **Kennzeichnung aller Threads aufheben**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie im Fenster "Debuggen" die Schaltfläche "Kennzeichnen" aus.  
  
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
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md)
