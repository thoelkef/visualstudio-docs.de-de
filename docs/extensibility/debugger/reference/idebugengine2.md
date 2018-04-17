---
title: IDebugEngine2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2cfe7e2f54b45ecfe8fdb34943b87818a13feab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2"></a>IDebugEngine2
Diese Schnittstelle stellt eine Debugging-Modul (DE). Es wird verwendet, um verschiedene Aspekte einer Debugsitzung zu verwalten, Haltepunkte festlegen und Löschen von Ausnahmen zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch eine benutzerdefinierte DE zum Debuggen von Programmen verwalten implementiert. Diese Schnittstelle muss von der DE implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird von der Sitzung Debug-Manager (SDM) zum Verwalten der Debugsitzung erfolgen, einschließlich Verwalten von Ausnahmen, erstellen Haltepunkte und reagieren auf synchrone Ereignisse per DE aufgerufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEngine2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Erstellt einen Enumerator für alle Programme, die von einer bereitgestellten Kompatibilitätsrichtlinie gedebuggt wird.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Fügt eine bereitgestellten Kompatibilitätsrichtlinie an ein Programm an.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Erstellt einen ausstehenden Haltepunkt in der Deutschland.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Gibt an, wie die DE für eine bestimmte Ausnahme behandeln soll.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Entfernt die angegebene Ausnahme an, sodass es nicht mehr durch die Debugging-Modul verarbeitet wird.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Entfernt die Liste der Ausnahmen, die für eine bestimmte Laufzeit-Architektur oder die Sprache die IDE festgelegt hat.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ruft die GUID des DE ab.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informiert die eine bereitgestellten Kompatibilitätsrichtlinie, die angegebene Programm ungewöhnlich beendet wurde und dass die DE bereinigen Sie alle Verweise auf das Programm und senden Sie ein Programm sollte, zerstören Ereignis.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wird aufgerufen, durch die SDM, um anzugeben, dass ein synchrone Debug-Ereignis, das zuvor von der DE gesendet, um die SDM empfangen und verarbeitet wurde.|  
|[setLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Legt das Gebietsschema des DE fest.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Legt den Registrierungsstamm, die derzeit in Verwendung durch die DE fest.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Legt eine Metrik an.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Fordert an, dass alle von diesem DE gedebuggten Programme beenden Ausführung das nächste Mal versucht, einen von ihrer Threads auszuführen.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)