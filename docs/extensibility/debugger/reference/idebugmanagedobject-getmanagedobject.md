---
title: "IDebugManagedObject::GetManagedObject | Microsoft Docs"
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
  - "IDebugManagedObject::GetManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::GetManagedObject-Methode"
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Schnittstelle zurück, die das verwaltete Objekt darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### Parameter  
 `ppManagedObject`  
 \[out\]  Gibt eine Schnittstelle zurück, die das verwaltete Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Schnittstelle, die von dieser Methode zurückgegeben wird, kann für jede Schnittstelle abgefragt werden, die durch die verwaltete Klasse implementiert ist und seine Methoden können aufgerufen werden soll.  
  
## Siehe auch  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)