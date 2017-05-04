---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
Gibt die Debug\- Anwendungsobjekt zurück, das dieser Skriptsite zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Parameter  
 `ppda`  
 \[out\] Zeiger Debug Anwendungsobjekt mit der Skriptsite zugeordnet.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host nicht direkt unterstützt das Debuggen.|  
  
## Hinweise  
 Die `GetApplication`\-Methode ermöglicht, dass ein Smarthost das Anwendungsobjekt definiert, der jedes Skript gehört.  Skriptmodule sollten versuchen, diese Methode aufrufen, um ihre enthaltene Anwendung und Rücksortierung an `IProcessDebugManager::GetDefaultApplication` abzurufen, wenn dies fehlschlägt.  
  
## Siehe auch  
 [IActiveScriptSiteDebug\-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)