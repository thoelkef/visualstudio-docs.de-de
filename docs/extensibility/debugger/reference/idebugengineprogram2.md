---
title: IDebugEngineProgram2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff075605371d39f9d3ff04df01c7022c52e809ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112222"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Diese Schnittstelle bietet Multithread-debugging-Unterstützung.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle, um das gleichzeitige Debuggen von mehreren Threads unterstützen. Diese Schnittstelle wird implementiert, auf das gleiche Objekt, implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) beim Abrufen dieser Schnittstelle aus einem `IDebugProgram2` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEngineProgram2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die an diesem Programm ausgeführt wird.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Überwacht die Ausführung (oder beenden, die für die Ausführung beobachten) an den angegebenen Thread ausgeführt.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Auswertung von Ausdrücken für den angegebenen Thread ausgeführt wird, auch wenn das Programm beendet wird ermöglicht (oder lässt nicht zu).|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio aufgerufen werden, diese Schnittstelle als Antwort auf eine [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis und die "Watch für Thread Schritt" und "Überwachen für Ausdruck Auswertung auf Thread" Status des Programms festlegen. [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, wenn das Programm beendet werden soll; diese Methode hat das Programm die Möglichkeit, die alle Threads zu beenden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)