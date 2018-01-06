---
title: "Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggings | Microsoft Docs"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0710bad95484ada62faa042edabf5b76ac459558
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Vorgehensweise: Wechseln Sie zu einem anderen Thread während des Debuggens in Visual Studio
Beim Debuggen einer Multithreadanwendung können Sie eine von mehreren Methoden verwenden, um als den Thread zu wechseln, die Sie an einen anderen Thread gearbeitet haben.

> [!NOTE]
> Wenn Sie die Reihenfolge steuern, in denen Threads ausführen, möchten, müssen Sie [Einfrieren und Reaktivieren von Threads](../debugger/get-started-debugging-multithreaded-apps.md).

Bei der Überprüfung der Threads im Code-Editor und die anderen Multithread-debugging-Fenster, gibt der gelbe Pfeil des aktuellen Threads an. Ein grüner Pfeil in Form einer Welle gibt an, dass ein nicht-aktuellen Thread der aktuelle Kontext des Debuggers verfügt.
  
### <a name="to-switch-to-any-thread-that-appears"></a>So wechseln Sie an einen beliebigen Thread, der angezeigt wird 
  
-   In der **Threads** oder **parallele Überwachung** Fenster, doppelklicken Sie auf den Thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>So wechseln Sie zu einem Thread in einem Quellcodefenster  
  
-   Im linken Bundsteg mit der Maustaste ein Symbol "Thread-Marker" ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker"), zeigen Sie auf **wechseln Sie zur**, und klicken Sie dann auf den Namen des Threads, zu dem Sie wechseln möchten, . Im Kontextmenü werden nur die Threads an dieser bestimmten Position angezeigt.  
  
     Wenn keine Threadmarker angezeigt, mit der Maustaste in den **Threads** Fenster, und überprüfen Sie, ob **Threads in Quelle anzeigen** ausgewählt ist.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>So wechseln Sie über die Symbolleiste Debugspeicherort zu einem Thread  
  
1.  Auf der **Debugspeicherort** -Symbolleiste klicken Sie auf die **Thread** Liste.  
  
2.  Klicken Sie in der Liste auf den Thread, zu dem Sie wechseln möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
