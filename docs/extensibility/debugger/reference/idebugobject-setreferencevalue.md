---
title: "IDebugObject::SetReferenceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::SetReferenceValue"
helpviewer_keywords: 
  - "IDebugObject::SetReferenceValue-Methode"
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Verweiswert dieses Objekts fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```c#  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### Parameter  
 `pObject`  
 \[in\]  Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt, das den neuen Verweiswert darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode übernimmt dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt einen Verweis auf den Wert des angegebenen Objekts in `pObject`\-Parameter und löst alle vorherigen Verweis aus.  Beachten Sie, dass dieses `IDebugObject`\-Objekt bereits ein Referenztyp sein muss.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)