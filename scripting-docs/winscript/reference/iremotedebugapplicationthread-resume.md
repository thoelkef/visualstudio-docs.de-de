---
title: "IRemoteDebugApplicationThread::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Resume"
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Resume
Setzt den Thread fortgesetzt.  
  
## Syntax  
  
```  
HRESULT Resume(  
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
 Wenn diese Methode den Thread fortgesetzt, setzt sie den Unterbrechungszähler.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)