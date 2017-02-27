---
title: "IDebugArrayObject::GetElement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetElement"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElement-Methode"
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft ein Element des Arrays ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```c#  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### Parameter  
 `dwIndex`  
 \[in\]  Der Elementindex.  
  
 `ppElement`  
 \[out\]  Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Schnittstelle zurück, mit der das Element darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode erkennt alle Elemente eines Arrayobjekts als eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensional ist.  Beispielsweise würde das Array `myarray[3][2][6]` und ein `dwIndex`\-Parameter von 20, diese Methode das Element aus `myarray[1][1][2]`zurückgegeben, und ein `dwIndex`\-Parameter von 21 wird das Element aus `myarray[1][1][3]`zurückgeben.  Verwenden Sie die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)\-Methode die Gesamtzahl der Elemente im Array zu bestimmen.  
  
## Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)