---
title: "IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor-Methode"
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Objekt ohne Konstruktor.  
  
## Syntax  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `pClassObject`  
 \[in\]  Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das den Typ des zu erstellenden Objekts darstellt.  
  
 `ppObject`  
 \[out\]  Gibt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Struktur oder eines komplexen Typs darstellt \(\) erfordert keinen Konstruktor, dass ein Parameter der Funktion ist, die von der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle dargestellt wird.  
  
 Wenn der Objektparameter einen Konstruktor erfordert, rufen Sie die [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)