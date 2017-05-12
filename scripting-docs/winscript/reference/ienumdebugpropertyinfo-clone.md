---
title: "IEnumDebugPropertyInfo::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Clone"
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```  
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\] Gibt die geklonte `IEnumDebugPropertyInfo`\-Schnittstelle zurück.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)