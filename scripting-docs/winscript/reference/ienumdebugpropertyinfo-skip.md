---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
Überspringt eine angegebene Anzahl `DebugPropertyInfo`\-Strukturen in einer Enumerationsfolge.  
  
## Syntax  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von `DebugPropertyInfo`\-Strukturen in der Enumerationsfolge zu überspringen.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  Gibt `S_FALSE` zurück und legt den Zeiger des aktuellen Elements am Ende der Enumeration, wenn `celt` größer ist, als Anzahl von Elementen fest, die im Enumerator verbleiben.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)