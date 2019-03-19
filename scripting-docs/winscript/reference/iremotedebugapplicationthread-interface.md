---
title: IRemoteDebugApplicationThread-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationThread interface
ms.assetid: 062bb997-7b9e-4945-bfbe-d5b92d5cb707
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd0574fe6093c6d53a63dfbbc97a7a313eaedc5f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160000"
---
# <a name="iremotedebugapplicationthread-interface"></a>IRemoteDebugApplicationThread-Schnittstelle
Stellt einen Ausführungsthread innerhalb einer bestimmten Anwendung dar.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplicationThread` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplicationThread::GetSystemThreadId](../../winscript/reference/iremotedebugapplicationthread-getsystemthreadid.md)|Gibt einen Betriebssystem-abhängige-Bezeichner, der dem Thread zugeordnet.|  
|[IRemoteDebugApplicationThread::GetApplication](../../winscript/reference/iremotedebugapplicationthread-getapplication.md)|Gibt zurück, die Application-Objekt, das diesem Thread zugeordnet.|  
|[IRemoteDebugApplicationThread::EnumStackFrames](../../winscript/reference/iremotedebugapplicationthread-enumstackframes.md)|Gibt einen Enumerator für den Stapelrahmen, der diesem Thread zugeordnet.|  
|[IRemoteDebugApplicationThread::GetDescription](../../winscript/reference/iremotedebugapplicationthread-getdescription.md)|Ruft die Beschreibung und den Zustand dieses Threads ab.|  
|[IRemoteDebugApplicationThread::SetNextStatement](../../winscript/reference/iremotedebugapplicationthread-setnextstatement.md)|Erzwingt, dass die Ausführung so nah wie möglich an den angegebenen Code-Kontext, in dem Kontext des angegebenen Rahmens fortgesetzt.|  
|[IRemoteDebugApplicationThread::GetState](../../winscript/reference/iremotedebugapplicationthread-getstate.md)|Ruft den Zustand dieses Threads.|  
|[IRemoteDebugApplicationThread::Suspend](../../winscript/reference/iremotedebugapplicationthread-suspend.md)|Hält den Thread.|  
|[IRemoteDebugApplicationThread::Resume](../../winscript/reference/iremotedebugapplicationthread-resume.md)|Wird den Thread fortgesetzt.|  
|[IRemoteDebugApplicationThread::GetSuspendCount](../../winscript/reference/iremotedebugapplicationthread-getsuspendcount.md)|Gibt den Unterbrechungszähler des Threads zurück.|