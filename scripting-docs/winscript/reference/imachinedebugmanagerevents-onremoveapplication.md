---
title: "IMachineDebugManagerEvents::onRemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerEvents.onRemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerEvents::onRemoveApplication"
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents::onRemoveApplication
Behandelt das Ereignis, wenn eine Anwendung von der Liste der laufenden Anwendung entfernt wird.  
  
## Syntax  
  
```  
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Anwendung, die aus der Liste der laufenden Anwendung entfernt wurde.  
  
 `dwAppCookie`  
 \[in\] Das Cookie bereitgestellt, als die Anwendung von der Anwendungsliste hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt an, dass eine Anwendung aus der Liste der laufenden Anwendung entfernt wurde.  
  
## Siehe auch  
 [IMachineDebugManagerEvents\-Schnittstelle](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)