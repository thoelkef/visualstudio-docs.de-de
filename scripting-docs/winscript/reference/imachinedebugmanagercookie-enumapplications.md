---
title: "IMachineDebugManagerCookie::EnumApplications | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::EnumApplications"
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::EnumApplications
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
 [IMachineDebugManagerCookie\-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)