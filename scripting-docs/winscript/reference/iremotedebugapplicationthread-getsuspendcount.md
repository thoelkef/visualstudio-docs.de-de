---
title: "IRemoteDebugApplicationThread::GetSuspendCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetSuspendCount
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetSuspendCount"
ms.assetid: 37f9936c-fd7c-412d-9a7f-628ca3a90438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetSuspendCount
Gibt den Unterbrechungszähler für den Thread zurück.  
  
## Syntax  
  
```  
HRESULT GetSuspendCount(  
   DWORD*  pdwCount  
);  
```  
  
#### Parameter  
 `pdwCount`  
 \[out\] Der Unterbrechungszähler für den Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den Unterbrechungszähler für den Thread zurück.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)