---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointErrorEvent2
helpviewer_keywords: IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 244a3d2c522d96983cf976b37ab206f2721d4e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Diese Schnittstelle weist dem Sitzungs-Manager (SDM), ein ausstehender Haltepunkt an einem geladenen Programm aufgrund einer Warnung oder einen Fehler nicht gebunden werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie diese Schnittstelle (verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt, wenn ein ausstehender Haltepunkt an der gedebuggten Anwendung gebunden werden kann. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM angegeben werden, wenn es an das derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBreakpointErrorEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ruft die [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Schnittstelle, die die Warnung oder den Fehler beschreibt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie ein Haltepunkt gebunden ist, wird ein Ereignis an die SDM gesendet. Wenn der Haltepunkt gebunden werden, ein `IDebugBreakpointErrorEvent2` gesendet wurde, andernfalls wird ein [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gesendet wird.  
  
 Beispielsweise fällt zu analysieren oder für die Auswertung die Bedingung zugeordneten ausstehenden Haltepunkts wird eine Warnung gesendet, dass die ausstehenden Haltepunkts zu diesem Zeitpunkt nicht gebunden werden kann. Dies kann auftreten, wenn der Code für den Haltepunkt noch nicht geladen wurde.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)