---
title: "IEnumDebugExtendedPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::GetCount"
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::GetCount
Ruft die Anzahl der `ExtendedDebugPropertyInfo`\-Strukturen im Enumerator ab.  
  
## Syntax  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### Parameter  
 `pcelt`  
 \[out\] Gibt die Anzahl der `ExtendedDebugPropertyInfo`\-Strukturen im Enumerator zurück.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IEnumDebugExtendedPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo\-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)