---
title: "IDebugCustomAttribute::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetName"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetName"
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des benutzerdefinierten Attributs ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```c#  
int GetName(  
   out string bstrName  
);  
```  
  
#### Parameter  
 `bstrName`  
 \[out\]  Gibt eine Zeichenfolge zurück, die den Namen des benutzerdefinierten Attributs enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Benannt Rückgabe von dieser Methode entspricht dem Namen der Klasse, die verwendet wird, um das Attribut zu deklarieren.  Dies entspricht möglicherweise nicht genau den Namen der benutzerdefinierten Attributklasse „C\# als auch über einen benutzerdefinierten Attributnamen können zu verwerfenden Suffix“ \- Attribut, wenn es in einer Deklaration verwendet wird.  
  
## Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)