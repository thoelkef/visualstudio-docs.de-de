---
title: IDebugThread2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2
helpviewer_keywords: IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dca773ca63e2ab6bbc852648d2dea92b0b9813d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2"></a>IDebugThread2
Diese Schnittstelle stellt einen Thread in einem Programm ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um einen Thread der Ausführung in einem einzelnen Programm darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) beim Abrufen dieser Schnittstelle, die den derzeit aktiven Thread darstellt.  
  
 Diese Schnittstelle wird auch bei der Erstellung einer Anforderung Haltepunkt verwendet (siehe [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Diese Schnittstelle wird auch zurückgegeben, wenn einen Haltepunkt gebunden oder Fehler zu beheben (siehe [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) und [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugThread2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Ruft eine Liste der Stapelrahmen für diesen Thread ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ruft den Namen des Threads ab.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Legt den Namen des Threads.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ruft die Anwendung, in der ein Thread ausgeführt wird.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Bestimmt, ob die nächste Anweisung an den bestimmten Stapelrahmen Frame- und Code Kontext festgelegt werden kann.|  
|[Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Legt die nächste Anweisung an den bestimmten Stapelrahmen Frame- und Code-Kontext fest.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ruft den Threadbezeichner des Systems ab.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Unterbricht einen Thread.|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Wird einen Thread fortgesetzt.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ruft die Eigenschaften, die einen Thread zu beschreiben.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ruft den logischen Thread dieser physischen Thread zugeordnet.|  
  
## <a name="remarks"></a>Hinweise  
 Da ein einzelnen physischen Thread ausgeführt werden kann, in mehreren Programmen, die mehr als ein `IDebugThread2` aus mehr als ein Programm kann im selben physischen Thread darstellen.  
  
 Wenn ein Breakpoint oder Ausnahme auftritt, wird ein Ereignis gesendet, durch den Aufruf [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Eines der Argumente an diese Methode ist ein `IDebugThread2` Schnittstelle, die den aktuellen Thread darstellt. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) wird zum Abrufen der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle für den aktuellen Stapelrahmen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)