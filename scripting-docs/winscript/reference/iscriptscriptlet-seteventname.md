---
title: "IScriptScriptlet::SetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetEventName"
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IScriptScriptlet::SetEventName
Legt den Namen des Ereignisses fest, das mit dem Skriptlet zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parameter  
 `psz`  
 \[in\] Ein Puffer, der den Ereignisnamen enthält, der mit dem `IScriptScriptlet`\-Objekt zugeordnet ist.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptScriptlet\-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)