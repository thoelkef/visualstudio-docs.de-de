---
title: "IEnumCodePaths2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Skip"
helpviewer_keywords: 
  - "IEnumCodePaths2::Skip"
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumCodePaths2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Überspringt die angegebene Anzahl von Elementen.  
  
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
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)