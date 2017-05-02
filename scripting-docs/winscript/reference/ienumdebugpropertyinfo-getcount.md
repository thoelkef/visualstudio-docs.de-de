---
title: "IEnumDebugPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::GetCount"
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::GetCount
Ruft die Anzahl der `DebugPropertyInfo`\-Strukturen im Enumerator ab.  
  
## Syntax  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### Parameter  
 `pcelt`  
 \[out\] Gibt die Anzahl der `DebugPropertyInfo`\-Strukturen im Enumerator zurück.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)