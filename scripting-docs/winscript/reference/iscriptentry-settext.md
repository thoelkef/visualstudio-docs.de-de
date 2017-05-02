---
title: "IScriptEntry::SetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ISetEntry::SetText"
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::SetText
Legt den Text, der einem `IScriptEntry` Skriptblock entspricht, oder den Quellcode fest, der in einem `IScriptScriptlet`\-Ereignishandler enthalten ist.  
  
## Syntax  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### Parameter  
 `psz`  
 \[in\] Der Text des `IScriptEntry` Skriptblocks oder der Quellcode des `IScriptScriptlet`\-Ereignishandlers.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)