---
title: "IDebugObject::IsNullReference | Microsoft Docs"
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
  - "IDebugObject::IsNullReference"
helpviewer_keywords: 
  - "IDebugObject::IsNullReference-Methode"
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Überprüft, ob das Objekt ein NULL\-Verweis ist.  
  
## Syntax  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```c#  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### Parameter  
 `pfIsNull`  
 \[out\]  Gibt Wert ungleich 0 \(null\) zurück \(`TRUE`\), wenn dieses Objekt ein NULL\-Verweis ist. Andernfalls gibt Null zurück \(`FALSE`\).  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein NULL\-Verweis ist ein leeres Objekt oder ein Objekt, das nicht zugewiesen wurde.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)