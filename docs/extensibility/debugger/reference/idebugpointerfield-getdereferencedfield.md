---
title: "IDebugPointerField::GetDereferencedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField::GetDereferencedField"
helpviewer_keywords: 
  - "IDebugPointerField::GetDereferencedField-Methode"
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt den Typ des Objekts zurück, auf das Objektpunkte des Zeigers.  
  
## Syntax  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Typ des Zielobjekts beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn z. B. die [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)\-Objektpunkte auf eine ganze Zahl, der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Typ, der von dieser Methode zurückgegeben wird, beschreibt, dass eine ganze Zahl eingeben.  
  
## Siehe auch  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)