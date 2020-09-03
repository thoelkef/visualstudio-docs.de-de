---
title: IDebugEngineLaunch2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbe76d800be035bc39caa477955b91bf21c074e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195672"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wird von einer Debug-Engine (de) zum Starten und Beenden von Programmen verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von einem benutzerdefinierten de implementiert, wenn Sie besondere Anforderungen für das Starten eines Prozesses hat, der nicht vollständig von einem benutzerdefinierten Port verarbeitet werden kann. Dies ist in der Regel der Fall, wenn die de Teil eines interpreters ist und der Prozess, der debuggt wird, ein Skript ist: der Interpreter muss zuerst gestartet werden, und das Skript wird geladen und gestartet. Der Interpreter kann von einem Port gestartet werden, aber das Skript erfordert möglicherweise eine besondere Behandlung (d. h., die Rolle hat eine Rolle). Diese Schnittstelle ist nur implementiert, wenn es besondere Anforderungen für das Starten eines Programms gibt, das von einem benutzerdefinierten Port nicht verarbeitet werden kann.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird vom Sitzungs-Debug-Manager (SDM) aufgerufen, wenn die SDM diese Schnittstelle von der [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle (mithilfe von QueryInterface) abrufen kann. Wenn diese Schnittstelle abgerufen werden kann, weiß der SDM, dass die de besondere Anforderungen hat, und ruft diese Schnittstelle auf, um das Programm zu starten, anstatt den Port zu starten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEngineLaunch2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Starten eines Prozesses mithilfe von de.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Nimmt die Prozess Ausführung wieder auf.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Beendet einen Prozess.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
