---
title: "IDebugArrayField::GetElementType | Microsoft Docs"
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
  - "IDebugArrayField::GetElementType"
helpviewer_keywords: 
  - "IDebugArrayField::GetElementType-Methode"
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Typ des Elements im Array ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### Parameter  
 `ppType`  
 \[out\]  Gibt ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt zurück, das den Typ des Elements beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)\-Objekt wird davon ausgegangen, dass alle Elemente des Arrays vom gleichen Typ aufweisen.  
  
## Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)