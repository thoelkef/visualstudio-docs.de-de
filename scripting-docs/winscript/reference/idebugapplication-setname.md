---
title: "IDebugApplication::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SetName"
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SetName
Legt den Namen der Anwendung fest.  
  
## Syntax  
  
```  
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### Parameter  
 `pstrName`  
 \[in\] Der Name der Anwendung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Name, der dieser Methode angegeben wird, wird in nachfolgenden Aufrufen der `IRemoteDebugApplication::GetName`\-Methode zurückgegeben.  
  
 Diese Methode sollte aufgerufen werden, bevor die `IProcessDebugManager::AddApplication`\-Methode aufruft.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)