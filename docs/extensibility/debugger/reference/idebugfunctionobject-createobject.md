---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObject-Methode"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Objekt unter Verwendung eines Konstruktors.  
  
## Syntax  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### Parameter  
 `pConstructor`  
 \[in\]  Ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Objekt, das den Konstruktor des zu erstellenden Objekts darstellt.  
  
 `dwArgs`  
 \[in\]  Die Anzahl von Parametern im`pArg` Array.  Stellt die Anzahl von Parametern dar, die an den Konstruktor übergeben werden.  
  
 `pArg`  
 \[in\]  Ein Array [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekten, die die Parameter darstellen, die an den Konstruktor übergeben.  
  
 `ppObject`  
 \[out\]  Gibt `IDebugObject` zurück, das das neu erstellte Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Klasse darstellt \(oder anderen komplexen Typs, der einen Konstruktor erfordert, dass ein Parameter der Funktion ist, die von der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle dargestellt wird.  
  
 Wenn der Objektparameter keinen Konstruktor erfordert, rufen Sie die [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)