---
title: "IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs"
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
  - "IDebugEnumField::GetUnderlyingSymbol"
helpviewer_keywords: 
  - "IDebugEnumField::GetUnderlyingSymbol-Methode"
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, die den Namen der Enumeration darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, der den Namen dieser Enumeration beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Name der Enumeration enthält auch den Typ der Enumeration, die an einer bestimmten Speicheradresse gebunden wird, indem Sie [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)verwendet.  
  
## Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)