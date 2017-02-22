---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
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
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArguments-Methode"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft eine Liste der Argumenttypen ab, die diesem Objekt zugeordnet sind.  
  
## Syntax  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### Parameter  
 `skip`  
 \[in\]Bevor Zahl Felder zu überspringen, Argumenttypen abgerufen werden.  
  
 `count`  
 \[in\]  Die Anzahl der zurückzugebenden Feldern Argument \(gibt außerdem die Größe des Arrays `ppFields` \).  
  
 `ppFields`  
 \[in, out\]  Ein Array von Feldern, die bei Rückgabe dieser Methode aufgefüllt werden.  
  
 `pFetched`  
 \[out\]  \(optional\) Die Anzahl der den Argumenttyp Felder, die tatsächlich zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Anzahl von Argumenttypen kann mit [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)vorab abgerufen werden.  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)