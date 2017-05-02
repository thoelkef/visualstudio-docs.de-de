---
title: "IProcessDebugManager::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::RemoveApplication"
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::RemoveApplication
Entfernt eine Anwendung aus der Liste der laufenden Anwendung.  
  
## Syntax  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### Parameter  
 `dwAppCookie`  
 \[in\] Das Cookie, das von `IProcessDebugManager::AddApplication` bereitgestellt wurde, als die Anwendung zur Anwendungsliste hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode entfernt eine Anwendung aus der Liste der laufenden Anwendung.  
  
## Siehe auch  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [IProcessDebugManager\-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)