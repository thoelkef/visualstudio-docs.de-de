---
title: "IDebugBinder::GetFunctionObject | Microsoft Docs"
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
  - "IDebugBinder::GetFunctionObject"
helpviewer_keywords: 
  - "IDebugBinder::GetFunctionObject-Methode"
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::GetFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Objekt ab, das zum Erstellungsfunktions parametern verwendet wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```c#  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### Parameter  
 `ppFunction`  
 \[out\]  Gibt die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle zurück, die den Erstellungsfunktions parametern verwendet wird.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)