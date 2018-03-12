---
title: IRemoteDebugApplicationEvents-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEvents interface
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04d40d3e03cfb9582075ec1be7abace963d1377f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationevents-interface"></a>IRemoteDebugApplicationEvents-Schnittstelle
Die `IRemoteDebugApplicationEvents` Schnittstelle ist die Ereignisschnittstelle, die von einem Debuganwendung bereitgestellt wird. Diese Schnittstelle wird immer vom Debugger Thread aus aufgerufen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplicationEvents` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|Ereignis wird behandelt ein Debugger verbunden.|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|Behandelt ein Debugger trennen Ereignis.|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|Ein Satz Name-Ereignis behandelt.|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|Verarbeitet ein Debuggerereignis für die Ausgabe an.|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|Behandelt das nach einer Anwendung schließen-Ereignis.|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|Behandelt ein Ereignis für die Eingabe eines Haltepunkts.|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|Behandelt ein Ereignis für einen Haltepunkt zu verlassen.|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|Verarbeitet eine Create-Thread-Ereignisses.|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|Behandelt ein Ereignis Thread zerstört.|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|Verarbeitet ein Ereignis, wenn die Unterbrechung Flags ändern.|