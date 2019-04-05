---
title: 'Vorgehensweise: Wechseln Sie zu einem anderen Thread während des Debuggings | Microsoft-Dokumentation'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fa84d46d64db048b58d0fcdb1c433b4830a5f45
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58955937"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Vorgehensweise: Wechseln Sie zu einem anderen Thread während des Debuggings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Debuggen einer Multithreadanwendung können Sie verschiedene Methoden verwenden, um vom Kontext des bearbeiteten Threads zu einem anderen Thread zu wechseln.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>So wechseln Sie zu einem Thread, der im Fenster Threads angezeigt wird  
  
-   Doppelklicken Sie auf den Thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>So wechseln Sie zu einem Thread in einem Quellcodefenster  
  
-   Klicken Sie im linken Bundsteg mit der rechten Maustaste eines Threadindikator, zeigen Sie auf **wechseln Sie zur**, und klicken Sie dann auf den Namen des Threads, zu dem Sie wechseln möchten. Im Kontextmenü werden nur die Threads an dieser bestimmten Position angezeigt.  
  
     Wenn keine Indikatoren angezeigt werden, mit der Maustaste in den **Threads** Fenster, und überprüfen Sie, ob **Threads in Quelle anzeigen** ausgewählt ist.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>So wechseln Sie über die Symbolleiste Debugspeicherort zu einem Thread  
  
1.  Auf der **Debugspeicherort** -Symbolleiste klicken Sie auf die **Thread** Feld.  
  
2.  Klicken Sie in der Liste auf den Thread, zu dem Sie wechseln möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
