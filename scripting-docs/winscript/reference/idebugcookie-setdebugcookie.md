---
title: "IDebugCookie::SetDebugCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugCookie::SetDebugCookie"
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCookie::SetDebugCookie
Legt das Debug\-Anwendungscookie fest.  
  
## Syntax  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### Parameter  
 `dwDebugAppCookie`  
 \[in\] Ein Cookie, das die Debugsitzung Anwendung identifiziert.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode legt die Debug\- Anwendungscookie fest, das mehr als einen Debugger die Anfügen an einen Prozess können.  
  
## Siehe auch  
 [IDebugCookie\-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)