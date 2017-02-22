---
title: "IDebugBinder::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::Bind"
helpviewer_keywords: 
  - "IDebugBinder::Bind-Methode"
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft den Arbeitsspeicher Elementkontext oder \- Objekt ab, das den aktuellen Wert des Symbols enthält.  
  
## Syntax  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `pContainer`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , das das untergeordnete Element enthält, durch `pField`verwiesen wird.  
  
 `pField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , das das Symbol darstellt.  
  
 `ppObject`  
 \[out\]  Gibt `IDebugObject` zurück, die die Instanz des Symbols darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)