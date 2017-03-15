---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveRuntimeType-Methode"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode bestimmt den Laufzeittyp eines Objekts.  
  
## Syntax  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### Parameter  
 `pObject`  
 \[in\]  Behoben werden soll [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .  
  
 `ppResolved`  
 \[out\]  Gibt den Typ des Objekts als [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Laufzeittyp eines Objekts zur Kompilierungszeit nicht immer bekannt.  Zum Beispiel für die Verwendung der Polymorphie, kann ein Argument für eine Funktion als Basisklasse, z. B. eine Schaltflächen \- Klasse übergeben werden.  Der tatsächliche Parameter könnte eine abgeleitete Klasse, z. B. eine Optionsfeld Klasse.  
  
## Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)