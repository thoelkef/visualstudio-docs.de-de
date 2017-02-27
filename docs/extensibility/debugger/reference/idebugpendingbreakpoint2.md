---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2-Schnittstelle"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Haltepunkt dar, der Code kann zu einem Speicherort zu binden.  
  
## Syntax  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) erstellt einen ausstehenden Haltepunkt aus einer [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)\-Schnittstelle.  Ein Aufruf von [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt eine `IDebugBreakpoint2`\-Schnittstelle, die einen gebundenen Haltepunkt im Programm darstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPendingBreakpoint2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob dieser ausstehende Haltepunkt zu einem Speicherort des Codes gebunden werden kann.|  
|[Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Umschließt den anstehenden Haltepunkt zu einem oder mehreren Code speicherorten.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand dieses anstehenden Haltepunkts ab.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft den Haltepunkt Anforderungen ab, die verwendet wurde, um den anstehenden Haltepunkt zu erstellen.|  
|[Virtualisieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Schaltet den virtualisierten Zustand dieses ausstehenden Haltepunkte um.|  
|[Aktivieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand des anstehenden Haltepunkts.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Legt die Änderungen oder Bedingung, die mit diesem ausstehenden Haltepunkt.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Anzahl der Änderungen übergeben oder legt diese fest, die mit diesem anstehenden Haltepunkt.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Haltepunkte auf, die von diesem anstehenden Haltepunkt gebunden sind.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler von Haltepunkten aufgelistet, die von diesem anstehenden Haltepunkt sich geführt haben.|  
|[Löschen](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht den anstehenden Haltepunkt, und alle Haltepunkte, die aus ihm gebunden sind.|  
  
## Hinweise  
 `IDebugPendingBreakpoint2` kann für einen Anbieter aller erforderlichen Informationen betrachtet werden, die benötigt werden, um einen Haltepunkt für Code, der auf einen angewendet werden kann oder mehreren Programmen zu binden.  
  
 Ein anstehender Haltepunkt kann mehr als einen gebundenen Haltepunkt möglicherweise erzeugen.  Beispielsweise kann ein Haltepunkt im C\-Format Vorlage in \+\+\-style einen gebundenen Haltepunkt für jede eindeutige Instanz dieser Vorlage erstellen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)