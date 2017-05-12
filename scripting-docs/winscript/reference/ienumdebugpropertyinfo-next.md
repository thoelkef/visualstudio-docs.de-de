---
title: "IEnumDebugPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Next"
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Next
Ruft eine angegebene Anzahl `DebugPropertyInfo`\-Strukturen in einer Enumerationsfolge ab.  
  
## Syntax  
  
```  
HRESULT Next (  
   ULONG celt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl der abzurufenden `DebugPropertyInfo`\-Strukturen.  
  
 `rgelt`  
 \[out\] Ein Array der abgerufenen `DebugPropertyInfo`\-Strukturen.  
  
 `pceltFetched`  
 \[out\] Gibt die Anzahl der tatsächlich abgerufenen `DebugPropertyInfo`\-Strukturen zurück.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)