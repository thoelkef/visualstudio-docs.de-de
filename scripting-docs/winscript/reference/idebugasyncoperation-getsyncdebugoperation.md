---
title: "IDebugAsyncOperation::GetSyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetSyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetSyncDebugOperation"
ms.assetid: ff89a3bc-57d7-4cb9-9818-8d73ed71af73
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetSyncDebugOperation
Gibt den synchronen Debugvorgang zurück, der diesem Objekt zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetSyncDebugOperation(  
   IDebugSyncOperation**  ppsdo  
);  
```  
  
#### Parameter  
 `ppsdo`  
 \[out\] Der synchrone Debugvorgang mit diesem Objekt verbunden.  
  
## Rückgabewert  
 Метод возвращает `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Hinweise  
 Diese Methode gibt den synchronen Debugvorgang zurück, der diesem Objekt zugeordnet ist.  
  
## Siehe auch  
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)