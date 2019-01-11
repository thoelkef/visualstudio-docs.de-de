---
title: IDebugStackFrame3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 376807a2963e93b3713d85b2d166c741671079bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932771"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Diese Schnittstelle erweitert [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , abgefangene Ausnahmen zu behandeln.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle zur Unterstützung von abgefangenen Ausnahmen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugStackFrame2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Behandelt eine Ausnahme für den aktuellen Stapelrahmen, bevor die reguläre Ausnahmebehandlung.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Gibt einen Codekontext an zurück, wenn es sich bei eine stapelentladung ausgeführt wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Eine abgefangene Ausnahme bedeutet, dass ein Debugger eine Ausnahme verarbeiten kann, bevor alle normalen Ausnahmebehandlung Routinen, die von der Laufzeit aufgerufen werden. Das Abfangen einer Ausnahme im Wesentlichen bedeutet, dass die Laufzeit nehmen, dass es ein Ausnahmehandler vorhanden, selbst wenn nicht vorhanden ist.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) während alle Ereignisse der normale Ausnahme-Rückruf aufgerufen wird (die einzige Ausnahme hierbei ist, wenn Sie in diesem Fall nicht die Ausnahme werden, während der abgefangen kann gemischten Code (verwaltet und nicht verwaltetem Code) Debuggen der letzte Gelegenheit Rückruf). Wenn die DE nicht implementiert `IDebugStackFrame3`, oder die DE gibt einen Fehler zurück, aus IDebugStackFrame3::`InterceptCurrentException` (wie z. B. `E_NOTIMPL`), und klicken Sie dann der Debugger normalerweise die Ausnahme behandelt.  
  
 Durch das Abfangen einer Ausnahme an, kann der Debugger kann den Benutzer Änderungen vornehmen, um den Status des gedebuggten Programm und dann die Ausführung an der Stelle, wo die Ausnahme ausgelöst wurde, fortgesetzt.  
  
> [!NOTE]
>  Abgefangene Ausnahmen sind nur in verwaltetem Code, also in einem Programm zulässig, die unter der Common Language Runtime (CLR) ausgeführt wird.  
  
 Eine Debug-Engine gibt an, dass es abfangender Ausnahmen unterstützt, durch Festlegen von "MetricExceptions" auf einen Wert von 1 zur Laufzeit mithilfe der `SetMetric` Funktion. Weitere Informationen finden Sie unter [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)