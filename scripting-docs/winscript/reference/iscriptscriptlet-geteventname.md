---
title: "IScriptScriptlet::GetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetEventName"
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IScriptScriptlet::GetEventName
Gibt den Namen des Ereignisses zurück, das mit dem Skriptlet zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Ein Puffer, der den Ereignisnamen enthält, der mit dem `IScriptScriptlet`\-Objekt zugeordnet ist.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptScriptlet\-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)