---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject-Methode"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine Kopie des verwalteten Objekts im Adressbereich des Debugmoduls.  
  
## Syntax  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### Parameter  
 `ppObject`  
 \[out\]  Gibt ein [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)\-Objekt zurück, das das neu erstellte verwaltete Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  Gibt E\_FAIL zurück, wenn dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) keine verwaltete Werts klasseninstanz darstellt.  
  
## Hinweise  
 Dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt muss eine verwaltete Werts klasseninstanz, wie eine `System.Decimal`\-Instanz darstellen.  Wenn Sie eine lokale Kopie der Mehraufwand des Aufrufs von [Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) wird beseitigt wurde.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)