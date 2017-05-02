---
title: "IRemoteDebugApplicationThread::Suspend | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Suspend
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Suspend"
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Suspend
Enthält den Thread an.  
  
## Syntax  
  
```  
HRESULT Suspend(  
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
 Wenn diese Methode den Thread enthält, erhöht sie den Unterbrechungszähler.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)