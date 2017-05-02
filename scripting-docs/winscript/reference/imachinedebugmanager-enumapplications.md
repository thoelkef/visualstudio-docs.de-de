---
title: "IMachineDebugManager::EnumApplications | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::EnumApplications"
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::EnumApplications
Gibt einen Enumerator der aktuellen Liste der ausgeführten Anwendungen zurück.  
  
## Syntax  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### Parameter  
 `ppeda`  
 \[out\] Enumerator, der die aktuelle Liste der ausgeführten Anwendungen enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt einen Enumerator der aktuellen Liste der ausgeführten Anwendungen zurück.  Der Debugger IDE verwendet diese Methode, um Anwendungen zu Debugzwecken anzuzeigen und anzufügen.  
  
## Siehe auch  
 [IMachineDebugManager\-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)