---
title: IDebugEventCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce30279cb58704ab712245ad69bcda197d0e7fc3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852757"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Diese Schnittstelle wird von der Debug-Engine (DE) verwendet, um Debug-Ereignisse an die sitzungsbasierter Debug-Manager (SDM) zu senden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert diese Schnittstelle zum Empfangen von Ereignissen aus einer Debug-Engine.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Eine Debug-Engine diese Schnittstelle in der Regel empfängt beim aufruft, des SDM [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md), oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Eine Debug-Engine sendet Ereignisse an das SDM, durch den Aufruf [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEventCallback2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet eine Benachrichtigung der Ereignisse an das SDM-Debuggen.|  
  
## <a name="remarks"></a>Hinweise  
 Obwohl [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) anzugeben, dass dafür ein `IDebugEventCallback2` -Schnittstelle, dies ist nicht der Fall ist, und der Schnittstellenzeiger wird immer ein null-Wert sein. Die Debug-Engine muss stattdessen die `IDebugEventCallback2` Schnittstelle empfangen, die im Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md), oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Wenn ein Paket implementiert [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code, es wird dringend empfohlen, die <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> aufgerufen werden, auf die verschiedenen Schnittstellen, die übergeben werden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)