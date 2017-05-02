---
title: "IRemoteDebugApplicationThread-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread-Schnittstelle"
ms.assetid: 062bb997-7b9e-4945-bfbe-d5b92d5cb707
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplicationThread-Schnittstelle
Stellt einen Ausführungsthread innerhalb einer bestimmten Anwendung dar.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IRemoteDebugApplicationThread`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplicationThread::GetSystemThreadId](../../winscript/reference/iremotedebugapplicationthread-getsystemthreadid.md)|Gibt einen anlagenspezifischen BetriebsBezeichner zurück, der mit dem Thread zugeordnet ist.|  
|[IRemoteDebugApplicationThread::GetApplication](../../winscript/reference/iremotedebugapplicationthread-getapplication.md)|Gibt das Anwendungsobjekt zurück, das diesem Thread zugeordnet ist.|  
|[IRemoteDebugApplicationThread::EnumStackFrames](../../winscript/reference/iremotedebugapplicationthread-enumstackframes.md)|Gibt einen Enumerator für die Stapelrahmen zurück, die diesem Thread zugeordnet werden.|  
|[IRemoteDebugApplicationThread::GetDescription](../../winscript/reference/iremotedebugapplicationthread-getdescription.md)|Ruft die Beschreibung und den Zustand dieses Threads ab.|  
|[IRemoteDebugApplicationThread::SetNextStatement](../../winscript/reference/iremotedebugapplicationthread-setnextstatement.md)|Kraftausführung, um der Vervollständigung so fortzusetzen, wie möglich an den angegebenen Codekontext, im Kontext des angegebenen Frames.|  
|[IRemoteDebugApplicationThread::GetState](../../winscript/reference/iremotedebugapplicationthread-getstate.md)|Ruft den Zustand des Threads ab.|  
|[IRemoteDebugApplicationThread::Suspend](../../winscript/reference/iremotedebugapplicationthread-suspend.md)|Enthält den Thread an.|  
|[IRemoteDebugApplicationThread::Resume](../../winscript/reference/iremotedebugapplicationthread-resume.md)|Setzt den Thread fortgesetzt.|  
|[IRemoteDebugApplicationThread::GetSuspendCount](../../winscript/reference/iremotedebugapplicationthread-getsuspendcount.md)|Gibt den Unterbrechungszähler für den Thread zurück.|