---
title: "Threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] threads"
  - "Threading [SDK-Debuggen]"
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Threads
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger **thread**:  
  
-   Ist die grundlegende Einheit der Berechnung mitgeführt wird.  Ein Thread wird sequenziell ihre Anweisungen im Kontext einer einzelnen Aufruflisten aus und wird von einem Code Elementkontext.  
  
-   Kann sich selbst und das Programm ermitteln, die es ausgeführt wird und kann benannt werden, angehalten und fortgesetzt werden.  Ein Thread kann die zugehörigen Stapelrahmen und unter verschiedenen Bedingungen ebenfalls aufgelistet werden, kann auf einen anderen Stapelrahmen verschoben werden.  Wenn der Kontext eines Stapelrahmens, kann ein Thread die zugeordneten logischen Thread zurückgegeben, sofern vorhanden.  Ein Thread verfügt über Eigenschaften, z. B. ein Unterbrechungszähler, der im Fenster Threads der IDE angezeigt werden kann.  
  
-   Wird von einer Schnittstelle dargestellt [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) erstellt, in der Regel durch eine Debug\- Modul \(DE\) oder virtuellen Computer als Folge der Ausführung eines Programms.  
  
## Siehe auch  
 [Programs](../../extensibility/debugger/programs.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Session\-Debug\-Manager](../../extensibility/debugger/session-debug-manager.md)