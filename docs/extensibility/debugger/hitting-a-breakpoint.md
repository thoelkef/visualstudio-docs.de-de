---
title: "Treffen eines Haltepunkts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], erreichen von Haltepunkten"
  - "Haltepunkte, drücken"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Treffen eines Haltepunkts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden wird der Prozess, wenn das Debugmodul \(DE\) ausgeführt werden, während ein Haltepunkt trifft, oder wenden:  
  
## Problembehandlung bei Erreichen eines Treffer\-Breakpoint  
  
1.  DE sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)\-Schnittstelle als **EVENT\_SYNCHRONIZATION\_STOP**.  
  
2.  Der Debuginformationen Manager der Sitzung \(SDM\) ruft [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den Haltepunkt zu erhalten, der ermittelt wurde.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)