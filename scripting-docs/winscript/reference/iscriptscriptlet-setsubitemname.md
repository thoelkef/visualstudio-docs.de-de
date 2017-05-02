---
title: "IScriptScriptlet::SetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSubItemName"
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptScriptlet::SetSubItemName
Legt den letzten Bezeichner im vollqualifizierten Namen des Objekthosts eines Skriptlets fest.  
  
## Syntax  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parameter  
 `psz`  
 Wenn der vollqualifizierte Skriptletname des Hosts mehr als eine Ebene verfügt, ist die `psz` Pufferadresse des Bezeichners auf der zweiten Ebene.  
  
 Wenn der vollqualifizierte Skriptletname des Hosts eine Ebene verfügt, ist die `psz` Pufferadresse des Bezeichners auf der ersten Ebene.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptScriptlet\-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)