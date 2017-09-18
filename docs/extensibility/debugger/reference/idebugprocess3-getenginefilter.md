---
title: "IDebugProcess3::GetEngineFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetEngineFilter"
  - "IDebugProcess3::GetEngineFilter"
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProcess3::GetEngineFilter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft ein Array von Modulen für verfügbare eindeutige Bezeichner ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```c#  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### Parameter  
 `pEngineArray`  
 \[out\]  Verweis auf eine Struktur, die eindeutige Bezeichner für die Module enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)