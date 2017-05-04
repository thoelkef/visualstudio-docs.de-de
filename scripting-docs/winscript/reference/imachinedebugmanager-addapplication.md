---
title: "IMachineDebugManager::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::AddApplication"
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::AddApplication
Fügt eine Anwendung der Liste der laufenden Anwendung hinzu.  
  
## Syntax  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Anwendung zur Liste der laufenden Anwendung.  
  
 `pdwAppCookie`  
 \[out\] Ein Cookie, das verwendet wird, um die Anwendung auf dem Computer Debug\- Manager zu entfernen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird vom Debuggen ProzessManager immer dann aufgerufen, wenn `IProcessDebugManager::AddApplication` aufgerufen wird.  
  
## Siehe auch  
 [IMachineDebugManager\-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)