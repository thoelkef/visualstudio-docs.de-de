---
title: "Wenn ein Haltepunkt gebunden bzw. wird aufgehoben | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] ungebundenen Haltepunkt Ereignisse"
  - "Haltepunkt gebunden Ereignisse"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Wenn ein Haltepunkt gebunden bzw. wird aufgehoben
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn ein Haltepunkt zu der Zeit nicht gebunden werden kann, wird ein Aufruf der [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)\-Methode durchgeführt und Zeit der Bindung, die Erstellungszeit des Haltepunkts unterschiedlich sind.  
  
## Methoden aufgerufen  
 Der Debuginformationen Manager der Sitzung \(SDM\) ruft die folgenden Methoden auf:  
  
1.  [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  DE [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)gibt diese zurück.  
  
2.  [IDebugPendingBreakpoint2::Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3.  [IDebugPendingBreakpoint2::Virtualisieren Sie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4.  Die [IDebugPendingBreakpoint2::Bindung](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)\-Methode und gibt S\_OK zurück.  DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) sendet oder [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5.  [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) und [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)\-Methoden, um die gebundenen Haltepunkte zu überprüfen und abzurufen.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)