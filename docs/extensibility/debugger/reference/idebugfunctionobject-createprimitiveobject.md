---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject-Methode"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein primitives Datenobjekt, wie eine einfache ganze Zahl.  
  
## Syntax  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `ot`  
 \[in\]  Ein Wert aus der [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md)\-Enumeration, der den Typ des zu erstellenden Grundtyps darstellt.  
  
 `ppObject`  
 \[out\]  Gibt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das ein primitives Objekt darstellt, das ein Parameter der Funktion ist, die von der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle dargestellt wird.  Wenn z. B. die Ausdruckszeichenfolge „myString \(5\)“, wird diese Methode verwendet, um ein Objekt zu erstellen, das die ganze Zahl 5 darstellt.  
  
## Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)