---
title: "L&#246;schen eines Haltepunktes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Löschen von Haltepunkten"
  - "Debuggen [Debugging-SDK], Löschen von Haltepunkten"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# L&#246;schen eines Haltepunktes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden wird der Prozess, wenn ein anstehender Haltepunkt gelöscht wird:  
  
## Löschen\-Prozess  
 Der Debuginformationen Manager der Sitzung \(SDM\) ruft die [IDebugPendingBreakpoint2::Löschen](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)\-Methode an, die den anstehenden Haltepunkt, und alle gebundenen Haltepunkte zu entfernen, die von ihm gebunden sind.  
  
> [!NOTE]
>  Ein einzelner gebundener Haltepunkt kann durch einen Aufruf an [IDebugBoundBreakpoint2::Löschen](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)ebenfalls gelöscht werden.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)