---
title: IDebugQueryEngine2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b32464084a209aa7d6f41ffaa837d2f377b9720a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984391"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Diese Schnittstelle kann die Sitzung mit dem Debug-Manager (SDM) rufen Sie eine Schnittstelle, die die Debug-Engine (DE) darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle für die Objekte, die die am häufigsten verwendeten DE-Schnittstellen zu implementieren (z. B. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), und [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) in Auftrag Zugriff auf die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle des DE selbst.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) an einer typischen DE-Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugQueryEngine2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft einen benutzerdefinierten Debug-Engine (DE)-Schnittstelle ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird in der Regel implementiert, in das Objekt, implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle zur Unterstützung von Kausalität geordnete Durchlaufen von Funktionen, d. h., wenn der Debugger aus einer Funktion, schrittweise Ausführung ist die die Next-Funktion zum Ausführen der previous-Funktion auf dem Stapel jedoch eine Funktion in einem anderen Thread vollständig möglicherweise nicht. Eine Definition von "Kausalität" finden Sie in der [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)