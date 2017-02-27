---
title: "IDebugFunctionObject::CreateStringObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateStringObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateStringObject-Methode"
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateStringObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Zeichenfolgenobjekt.  
  
## Syntax  
  
```cpp#  
HRESULT CreateStringObject(   
   LPCOLESTR      pcstrString,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateStringObject(  
   string      pcstrString,   
   out IDebugObject ppOjbect  
);  
```  
  
#### Parameter  
 `pcstrString`  
 \[in\]  Der Zeichenfolgenwert für das Zeichenfolgenobjekt.  
  
 `ppObject`  
 \[out\]  Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt zurück, das das neu erstellte Zeichenfolgenobjekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Zeichenfolge darstellt, die ein Parameter der Funktion ist, die von der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle dargestellt wird.  
  
## Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)