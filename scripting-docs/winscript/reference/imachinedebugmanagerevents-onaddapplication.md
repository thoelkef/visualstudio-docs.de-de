---
title: "IMachineDebugManagerEvents::onAddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerEvents.onAddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerEvents::onAddApplication"
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents::onAddApplication
Behandelt das Ereignis, wenn eine Anwendung zur Liste der laufenden Anwendung hinzugefügt wird.  
  
## Syntax  
  
```  
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Anwendung, die der Liste der laufenden Anwendung hinzugefügt wurde.  
  
 `dwAppCookie`  
 \[in\] Das Cookie, das bereitgestellt wird, als die Anwendung zur Anwendungsliste hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt an, dass eine Anwendung zur Liste der laufenden Anwendung hinzugefügt wurde.  
  
## Siehe auch  
 [IMachineDebugManagerEvents\-Schnittstelle](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)