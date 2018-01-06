---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2
helpviewer_keywords: IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc6dacbac1092e211ba129417bd4e47aea31b733
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Die Debugging-Modul (DE) sendet diese Schnittstelle an der Sitzung Debug-Manager (SDM), beim Auftreten einer Ausnahme in der Anwendung, die derzeit ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum angeben, in der Anwendung, der debuggt wird eine Ausnahme aufgetreten ist. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt eine Ausnahme gemeldet. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn diese an die derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExceptionEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ruft ausführliche Informationen über die Ausnahme, die dieses Ereignis ausgelöst hat.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ruft eine lesbare Beschreibung für die ausgelöste Ausnahme, die dieses Ereignis ausgelöst hat.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Legt fest, ob die Debugging-Modul (DE) die Möglichkeit, diese Ausnahme an die Anwendung gedebuggt wird unterstützt, wenn die Ausführung fortsetzt übergeben.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Gibt an, ob die Ausnahme übergeben werden soll, das Programm, das gerade gedebuggt wird, wenn die Ausführung fortsetzt, oder wenn die Ausnahme verworfen werden sollen.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Hinweise  
 Vor dem Senden des Ereignisses, die DE überprüft, ob diese Ausnahmeereignis eine erste Chance oder Sekunde Chance Ausnahme durch einen vorherigen Aufruf durchgehend [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Wenn er festgelegt wurde, um eine nicht abgefangene Ausnahme werden die `IDebugExceptionEvent2` Ereignis gesendet, um die SDM. Wenn dies nicht der Fall ist, die DE ermöglicht es einer Anwendung eine Möglichkeit zur Behandlung von Ausnahmen. Wenn keine Ausnahmehandler bereitgestellt wird und die Ausnahme als eine Ausnahme Sekunde Chance festgelegt wurde die `IDebugExceptionEvent2` Ereignis gesendet, um die SDM. Andernfalls die DE setzt die Ausführung des Programms, und das Betriebssystem oder die Runtime Ausnahmen behandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)