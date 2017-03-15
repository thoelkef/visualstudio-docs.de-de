---
title: "Haltepunkt-Fehler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Haltepunkte, Fehler"
  - "Haltepunkt-Debugfehler [Debugging-SDK]"
  - "Fehler [SDK-Debuggen]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Haltepunkt-Fehler
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden wird der Prozess, wenn ein Haltepunkt auf Code versucht zu binden, schlägt jedoch fehl:  
  
## Problembehandlung bei Erreichen eines Breakpoint\-Fehler  
  
1.  Das Debugmodul \(DE\) sendet [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) Debuggen auf den Manager der Sitzung \(SDM\).  
  
2.  Das [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(SDM ruft IDebugErrorBreakpoint2 \*\* `ppErrorBP`\) auf, um den Fehler breakpoint abzurufen.  
  
3.  Das SDM ruft [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) auf, um den ausstehenden Haltepunkt abzurufen, aus dem der Fehler breakpoint stammt.  
  
4.  Das SDM ruft [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) auf, um die Ursache zu erhalten, warum der Fehler breakpoint, der fehlgeschlagen ist.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)