---
title: "IDebugManagedObject::SetFromManagedObject | Microsoft Docs"
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
  - "IDebugManagedObject::SetFromManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::SetFromManagedObject-Methode"
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert der Instanz des Werts klassenobjekts aus der Instanz der Wertklasse fest, die als Parameter bereitgestellt wird.  
  
## Syntax  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```c#  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### Parameter  
 `pManagedObject`  
 \[in\]  Eine Schnittstelle, die das verwaltete Objekt darstellt, das den neuen Wert enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird verwendet, um das verwaltete Objekt zu ändern, wie durch das [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)\-Objekt dargestellt.  
  
## Siehe auch  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)