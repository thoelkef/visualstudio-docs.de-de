---
title: "IEnumDebugAddresses::Skip | Microsoft Docs"
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
  - "IEnumDebugAddresses::Skip"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Skip-Methode"
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugAddresses::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode über der angegebenen Anzahl von Elementen.  
  
## Syntax  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
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
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)