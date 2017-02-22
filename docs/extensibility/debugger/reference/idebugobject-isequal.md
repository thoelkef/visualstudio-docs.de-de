---
title: "IDebugObject::IsEqual | Microsoft Docs"
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
  - "IDebugObject::IsEqual"
helpviewer_keywords: 
  - "IDebugObject::IsEqual-Methode"
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vergleicht ein Objekt mit diesem Objekt.  
  
## Syntax  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```c#  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### Parameter  
 `pObject`  
 \[in\]  Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt, das das Objekt darstellt, die verglichen werden soll.  
  
 `pfIsEqual`  
 \[out\]  Gibt Wert ungleich 0 \(null\) zurück \(`TRUE`\), wenn die Werte der Objekte gleich sind. Andernfalls gibt Null zurück \(`FALSE`\).  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 In der Regel kann diese Methode die Adressen der Werte vergleichen, die vom `pObject`\-Parameter und dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt dargestellt werden. Wenn die Adressen gleich sind, können die Objekte als gleich betrachtet werden.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)