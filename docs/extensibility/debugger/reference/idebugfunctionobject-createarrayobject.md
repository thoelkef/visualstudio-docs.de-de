---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject-Methode"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Arrayobjekt.  Dieses Array kann entweder Grundtyp\- oder Objektinstanz Werte enthalten.  
  
## Syntax  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `ot`  
 \[in\]  Gibt einen Wert aus der [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md)\-Enumeration, die den Typ des neuen Arrayobjekts angibt.  
  
 `pClassField`  
 \[in\]  Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das die Klasse des Objekts darstellt, wenn ein Array von Werten Objektinstanz erstellt wird.  Wenn ein Array primitive Objekte erstellt, ist dieser Parameter ein NULL\-Wert.  
  
 `dwRank`  
 \[in\]  Der Rang oder die Anzahl der Dimensionen des Arrays.  
  
 `dwDims`  
 \[in\]  Die Größe jeder Dimension des Arrays.  
  
 `dwLowBounds`  
 \[in\]  Der Ursprung jeder Dimension \(in der Regel 0 oder 1\).  
  
 `ppObject`  
 \[out\]  Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt zurück, das das neu erstellte Array darstellt.  Hierbei handelt es sich eigentlich ein [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)\-Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das einen Arrayparameter der Funktion darstellt, die sowohl durch die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle dargestellt wird.  
  
## Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)