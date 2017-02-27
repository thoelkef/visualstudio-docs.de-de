---
title: "IDebugBinder::ResolveDynamicType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveDynamicType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveDynamicType-Methode"
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBinder::ResolveDynamicType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt den genauen Typ einer Variablen zurück.  
  
## Syntax  
  
```cpp#  
HRESULT ResolveDynamicType (  
   IDebugDynamicField *pDynamic,  
   IDebugField       **ppResolved  
);  
```  
  
```c#  
int ResolveDynamicType(  
   IDebugDynamicField pDynamic,   
   out IDebugField    ppResolved  
);  
```  
  
#### Parameter  
 `pDynamic`  
 \[in\]  [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) , das einen Typ Variable darstellt.  
  
 `ppResolved`  
 \[out\]  Gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, die bestimmte Informationen zum Typ der Variablen vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)