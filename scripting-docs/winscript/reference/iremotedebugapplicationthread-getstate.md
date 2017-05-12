---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
Ruft den Zustand des Threads ab.  
  
## Syntax  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### Parameter  
 `pState`  
 \[out\] kennzeichnet Kombination des folgenden Threadzustandes:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|THREAD\_STATE\_RUNNING|0x00000001|Der Thread ausgeführt wird.|  
|THREAD\_STATE\_SUSPENDED|0x00000002|Der Thread wurde angehalten.|  
|THREAD\_BLOCKED|0x00000004|Der Thread ist blockiert.|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|Der Thread ist aus Inhalt aus.|  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft den Zustand dieses Threads ab.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)