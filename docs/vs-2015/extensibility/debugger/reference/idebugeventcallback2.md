---
title: IDebugEventCallback2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163822"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird von der Debug-Engine (de) verwendet, um Debugereignisse an den Sitzungs-Debug-Manager (SDM) zu senden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementiert diese Schnittstelle zum Empfangen von Ereignissen von einer Debug-Engine.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Eine Debug-Engine empfängt diese Schnittstelle in der Regel, wenn die SDM [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten aufruft. Ein Debug-Modul sendet Ereignisse an die SDM, indem das [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)aufgerufen wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEventCallback2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet Benachrichtigungen über Debuggingereignisse an SDM.|  
  
## <a name="remarks"></a>Bemerkungen  
 Obwohl [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) angeben, dass eine `IDebugEventCallback2` Schnittstelle verwendet wird, ist dies nicht der Fall, und der Schnittstellen Zeiger ist immer ein NULL-Wert. Stattdessen muss die Debug-Engine die-Schnittstelle verwenden, die im-Befehl `IDebugEventCallback2` zum [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten empfangen wird.  
  
 Wenn ein Paket [idebugeventcallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code implementiert, wird dringend empfohlen, dass Sie <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> für die verschiedenen Schnittstellen aufgerufen werden, die an das- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)weitergegeben werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Launchangeh alten](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [An](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
