---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
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
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die ganz unten stehende Eigenschaft einer Eigenschaft ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### Parameter  
 `ppDerivedMost`  
 \[out\]  Gibt ein Objekt zurück, das die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ganz unten stehende Eigenschaft darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Gibt `S_GETDERIVEDMOST_NO_DERIVED_MOST` zurück, wenn keine ganz unten stehende Eigenschaft abgerufen wird.  
  
## Hinweise  
 Wenn beispielsweise die folgende Eigenschaft ein Objekt beschreibt, das `ClassRoot` implementiert, aber das tatsächlich eine Instanziierung von `ClassDerived` ist, die von `ClassRoot`abgeleitet ist, gibt diese Methode ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das das `ClassDerived`\-Objekt beschreibt.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)