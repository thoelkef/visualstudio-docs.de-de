---
title: "IDebugBinder3::GetTypeArgumentCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetTypeArgumentCount"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArgumentCount-Methode"
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetTypeArgumentCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt die Anzahl der Argumenttypen zurück, die diesem Objekt zugeordnet sind.  
  
## Syntax  
  
```cpp  
HRESULT GetTypeArgumentCount(  
   UINT* uCount  
);  
```  
  
```c#  
int GetTypeArgumentCount(  
   out uint uCount  
);  
```  
  
#### Parameter  
 `uCount`  
 \[out\]  Anzahl von Argumenttypen, die mit diesem Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der von dieser Methode zurückgegeben wird, kann verwendet werden, um ein Array zur Verwendung mit der [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)\-Methode zuzuordnen.  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)