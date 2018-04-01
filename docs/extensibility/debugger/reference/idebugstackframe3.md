---
title: IDebugStackFrame3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a45859fe78df3907df680b7716f743ff411ca3f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Diese Schnittstelle erweitert [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) abgefangene Ausnahmen zu behandeln.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle zur Unterstützung von abgefangenen Ausnahmen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugStackFrame2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Eine Ausnahme für den aktuellen Stapelrahmen vor jeder reguläre Ausnahmebehandlung behandelt.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Gibt einen Codekontext, wäre eine stapelentladung auftritt.|  
  
## <a name="remarks"></a>Hinweise  
 Eine abgefangene Ausnahme bedeutet, dass ein Debugger eine Ausnahme verarbeiten kann, bevor eine normale Ausnahme Ereignisbehandlungsroutinen von der Laufzeit aufgerufen werden. Im Wesentlichen wird eine Ausnahme abgefangen, sodass zur Laufzeit nehmen an, dass es ein Ausnahmehandler vorhanden, auch wenn nicht vorhanden ist.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) wird aufgerufen, während alle Rückrufereignisse für normale Ausnahme (die einzige Ausnahme hierbei ist im gemischten Modus (verwalteter und nicht verwaltetem Code), Debuggen von Code werden in diesem Fall nicht die Ausnahme werden, während abgefangen kann die letzte Chance Rückruf). Wenn DE nicht implementiert `IDebugStackFrame3`, oder die DE gibt einen Fehler zurück, aus IDebugStackFrame3::`InterceptCurrentException` (z. B. `E_NOTIMPL`), und klicken Sie dann der Debugger normalerweise die Ausnahme behandelt.  
  
 Durch das Abfangen einer Ausnahme, kann der Debugger können Benutzer Änderungen vornehmen, in den Zustand des Programms, der debuggt wird, und dann die Ausführung an der Stelle, wo die Ausnahme ausgelöst wurde, fortgesetzt.  
  
> [!NOTE]
>  Abgefangene Ausnahmen sind nur in verwaltetem Code, d. h. in einem Programm zulässig, die unter der Common Language Runtime (CLR) ausgeführt wird.  
  
 Ein Debugmodul gibt an, dass abgefangene Ausnahmen unterstützt wird, indem Sie die Einstellung "MetricExceptions" auf einen Wert von 1 zur Laufzeit mithilfe der `SetMetric` Funktion. Weitere Informationen finden Sie unter [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)