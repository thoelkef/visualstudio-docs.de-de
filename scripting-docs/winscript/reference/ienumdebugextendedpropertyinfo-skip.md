---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
Überspringt eine angegebene Anzahl `ExtendedDebugPropertyInfo`\-Strukturen in einer Enumerationsfolge.  
  
## Syntax  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von `ExtendedDebugPropertyInfo`\-Strukturen in der Enumerationsfolge zu überspringen.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  Gibt `S_FALSE` zurück und legt den Zeiger des aktuellen Elements am Ende der Enumeration, wenn `celt` größer ist, als Anzahl von Elementen fest, die im Enumerator verbleiben.  
  
## Siehe auch  
 [IEnumDebugExtendedPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo\-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)