---
title: "IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Next"
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Next
Ruft eine angegebene Anzahl `ExtendedDebugPropertyInfo`\-Strukturen in einer Enumerationsfolge ab.  
  
## Syntax  
  
```  
HRESULT Next (  
   ULONG celt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl der abzurufenden `ExtendedDebugPropertyInfo`\-Strukturen.  
  
 `rgelt`  
 \[out\] Ein Array der abgerufenen `ExtendedDebugPropertyInfo`\-Strukturen.  
  
 `pceltFetched`  
 \[out\] Die Anzahl der `ExtendedDebugPropertyInfo`\-Strukturen tatsächlich abgerufen.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IEnumDebugExtendedPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo\-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)