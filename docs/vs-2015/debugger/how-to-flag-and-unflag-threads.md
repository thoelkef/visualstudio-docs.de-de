---
title: 'Vorgehensweise: kennzeichnen und Kennzeichnung von Threads | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817489"
---
# <a name="how-to-flag-and-unflag-threads"></a>Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einen Thread, der besondere Aufmerksamkeit erhalten, indem Sie es mit einem Symbol im markieren möchten kennzeichnen die **Threads**, **parallele Stapel**, **parallele Überwachung**, und **GPU Threads** Windows. Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
 Gekennzeichnete Threads werden auch in eine besondere Behandlung der **Thread** auf in der Liste der **Debugspeicherort** Symbolleiste. In dieser Liste können alle Threads oder nur gekennzeichnete Threads aufgeführt werden. Wenn Sie einen Thread kennzeichnen die **Thread** Liste wechselt automatisch zum nur gekennzeichnete Threads anzeigen, aber Sie können es wechseln zurück, um alle Threads nach Bedarf anzuzeigen.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>So können Sie einen Thread mithilfe des Fensters Threads kennzeichnen oder seine Kennzeichnung aufheben  
  
-   In der **Threads** Fenster Suchen Sie den Thread, der Sie interessiert sind, und klicken Sie auf das Flaggensymbol klicken, aktivieren oder deaktivieren das Flag.  
  
### <a name="to-unflag-all-threads"></a>So heben Sie die Kennzeichnung aller Threads auf  
  
-   In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **Kennzeichnung aller Threads**.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie im Fenster "Debuggen" die Schaltfläche "Kennzeichnen" aus.  
  
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
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md)



