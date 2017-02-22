---
title: "IDebugObject::IsReadOnly | Microsoft Docs"
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
  - "IDebugObject::IsReadOnly"
helpviewer_keywords: 
  - "IDebugObject::IsReadOnly-Methode"
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob dieses Objekt schreibgeschützt ist.  
  
## Syntax  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```c#  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### Parameter  
 `pfIsReadOnly`  
 \[out\]  Gibt Wert ungleich 0 \(null\) zurück \(`TRUE`\), wenn dieses Objekt schreibgeschützt ist. Andernfalls gibt Null zurück \(`FALSE`\).  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein schreibgeschütztes Objekt kann den geänderten Wert nicht vorhanden ist, nachdem es erstellt wurde.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)