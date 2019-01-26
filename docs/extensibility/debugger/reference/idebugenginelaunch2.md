---
title: IDebugEngineLaunch2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 052ca349749d30a8e27c6104384fd2953c9e5162
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925980"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Wird von einer Debug-Engine (DE) zum Starten und Beenden von Programmen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch eine benutzerdefinierte DE implementiert, verfügt er spezielle Anforderungen zum Starten eines Prozesses, das vollständig von einem benutzerdefinierten Port nicht behandelt werden kann. Dies ist normalerweise der Fall, wenn die DE Teil eines Interpreters ist, und der gedebuggte Prozess ein Skript ist: der Interpreter muss zuerst gestartet werden, und klicken Sie dann das Skript geladen und gestartet. Ein Port den Interpreter starten, aber das Skript möglicherweise erfordern eine besondere Behandlung (Was ist, in denen die DE eine Rolle ist). Diese Schnittstelle wird implementiert, nur, wenn es sind besondere Anforderungen zum Starten eines Programms, das ein benutzerdefinierter Port nicht verarbeiten kann.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird aufgerufen, durch die sitzungsbasierter Debug-Manager (SDM) Wenn das SDM dieser Schnittstelle erhalten kann, aus der [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle (mit QueryInterface). Wenn diese Schnittstelle abgerufen werden kann, weiß das SDM an, dass der Code verfügt über spezielle Anforderungen und diese Schnittstelle ruft, um das Programm, statt den Port an, starten Sie ihn zu starten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEngineLaunch2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Startet einen Prozess, durch die DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Prozess wird fortgesetzt.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Beendet einen Prozess an.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)