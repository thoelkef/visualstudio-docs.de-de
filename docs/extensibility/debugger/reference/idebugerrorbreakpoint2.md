---
title: "IDebugErrorBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpoint2"
helpviewer_keywords: 
  - "IDebugErrorBreakpoint2-Schnittstelle"
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Fehler oder auf einen warnenden Haltepunkt, wie ein ungültiger Speicherort, ein ungültiger Ausdruck oder die Gründe, warum der ausstehenden Haltepunkt nicht gebunden ist \(der Code noch nicht geladen, usw.\).  
  
## Syntax  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Debuggen Modul implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Diese Schnittstelle wird verwendet, um Probleme mit dem Binden eines Haltepunkts.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) erhält diese Schnittstelle.  Diese Schnittstelle kann \(dargestellt als Teil einer Liste durch eine [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)\-Schnittstelle\) durch einen Aufruf von [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)auch zurückgegeben werden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugErrorBreakpoint2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den anstehenden Haltepunkt ab, der den Fehler verursacht hat.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die Auflösung von Fehlern Haltepunkt ab, die den Fehler beschreibt.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)