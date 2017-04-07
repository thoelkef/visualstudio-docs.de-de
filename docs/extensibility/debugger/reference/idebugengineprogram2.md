---
title: IDebugEngineProgram2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 2897213b9c94a2c8a140c12bfdbc3d4deb29052e
ms.lasthandoff: 04/05/2017

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
|[Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die an diesem Programm ausgeführt wird.|  
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
