---
title: "IMachineDebugManagerCookie::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.RemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::RemoveApplication"
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::RemoveApplication
Entfernt eine Anwendung aus der Liste der laufenden Anwendung.  
  
## Syntax  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### Parameter  
 `dwDebugAppCookie`  
 \[in\] Ein Cookie, das die Debugsitzung Anwendung identifiziert.  
  
 `dwAppCookie`  
 \[in\] Das Cookie, das bereitgestellt wird, als die Anwendung zur Anwendungsliste hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird vom Debuggen ProzessManager immer dann aufgerufen, wenn `IProcessDebugManager::RemoveApplication` aufgerufen wird.  
  
## Siehe auch  
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [IMachineDebugManagerCookie\-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)