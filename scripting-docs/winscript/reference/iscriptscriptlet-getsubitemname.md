---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
Gibt den letzten Bezeichner im vollqualifizierten Namen des Objekthosts eines Skriptlets zurück.  
  
## Syntax  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Wenn der vollqualifizierte Skriptletname des Hosts mehr als eine Ebene verfügt, gibt die `pbstr` Pufferadresse des Bezeichners auf der zweiten Ebene zurück.  
  
 Wenn der vollqualifizierte Skriptletname des Hosts eine Ebene verfügt, gibt die `pbstr` Pufferadresse des Bezeichners auf der ersten Ebene zurück.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptScriptlet\-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)