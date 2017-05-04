---
title: "IScriptScriptlet:: GetSimpleEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet. GetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSimpleEventName"
ms.assetid: 012eb555-b26c-4248-bbcc-fc30e6f2b308
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IScriptScriptlet:: GetSimpleEventName
Gibt den einfachen Ereignisnamen zurück, der mit einem Skriptlet zugeordnet ist.  Dies ist ein Einwortname, der keine Leerzeichen enthält.  
  
## Syntax  
  
```  
HRESULT GetSimpleEventName(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Ein Puffer, der den einfachen Ereignisnamen enthält, der mit dem `IScriptScriptlet`\-Objekt zugeordnet ist.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptScriptlet\-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)