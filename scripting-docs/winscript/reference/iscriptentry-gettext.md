---
title: "IScriptEntry::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetText"
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetText
Gibt den Text, der dem `IScriptEntry` Skriptblock entspricht, oder den Quellcode zurück, der im `IScriptScriptlet`\-Ereignishandler enthalten ist.  
  
## Syntax  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Der Text im `IScriptEntry` Skriptblock oder der Quellcode, der im `IScriptScriptlet`\-Ereignishandler enthalten ist.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)