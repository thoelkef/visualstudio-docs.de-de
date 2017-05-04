---
title: "IDebugFormatter::GetVariantForString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetVariantForString"
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetVariantForString
Gibt eine VARIANTE zurück, die die angegebene Zeichenfolge enthält.  
  
## Syntax  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### Parameter  
 `pwstrValue`  
 \[in\] in einer VARIANTE zu speichern, Zeichenfolge.  
  
 `pvar`  
 \[out\] VARIANTES enthaltendes `pwstrValue`.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt eine VARIANTE zurück, die die angegebene Zeichenfolge enthält.  
  
## Siehe auch  
 [IDebugFormatter\-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)