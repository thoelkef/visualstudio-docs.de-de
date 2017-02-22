---
title: "IEnumDebugFields::Skip | Microsoft Docs"
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
  - "IEnumDebugFields::Skip"
helpviewer_keywords: 
  - "IEnumDebugFields::Skip-Methode"
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode über der angegebenen Anzahl von Elementen.  
  
## Syntax  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der zu überspringenden Elemente.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` , wenn `celt` größer als die Anzahl der verbleibenden Elemente zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn `celt` einen Wert angibt, der von verbleibenden Elemente größer als die Anzahl ist, wird die Enumeration auf das Ende festgelegt und `S_FALSE` wird zurückgegeben.  
  
## Siehe auch  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)