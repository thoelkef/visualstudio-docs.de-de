---
title: IDebugErrorBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de2acab356ad31282e5a11cafd347867ca376258
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930134"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Diese Schnittstelle stellt einen Fehler oder Warnung Haltepunkt, z. B. die Gründe, warum der ausstehenden Haltepunkt (Code nicht geladen werden, noch usw.) nicht gebunden wurde, ein ungültiger Ausdruck oder einen ungültigen Speicherort.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte an. Diese Schnittstelle wird verwendet, um Probleme mit der Bindung eines Haltepunkts zu melden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) ruft diese Schnittstelle. Diese Schnittstelle auch zurückgegeben werden kann (als Teil einer Liste, dargestellt durch ein [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) Schnittstelle) durch einen Aufruf von [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugErrorBreakpoint2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt, der den Fehler verursacht hat.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft ab, das Haltepunkt-Fehlerbehebung, das den Fehler beschreibt.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)