---
title: "IRemoteDebugApplicationThread::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.EnumStackFrames
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::EnumStackFrames"
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::EnumStackFrames
Gibt einen Enumerator für die Stapelrahmen zurück, die diesem Thread zugeordnet werden.  
  
## Syntax  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parameter  
 `ppedsf`  
 \[out\] Einen Enumerator für die Stapelrahmen zugeordnet mit diesem Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode muss aus einem Haltepunkt aufgerufen werden.  Der Stapelrahmenenumerator sollte die Frames zurückgeben zuletzt beginnend am Anfang des Stapels, beginnend mit den gedrückten Frame.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)