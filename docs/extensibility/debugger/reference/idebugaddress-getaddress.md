---
title: "IDebugAddress::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress-Methode"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Struktur zurück, die auf ein Objekt und dessen Position innerhalb seines Bereichs oder Containers beschreibt.  
  
## Syntax  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in, out\]  Eine [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die so ausgefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur wird an diese Methode übergeben, die dann mit den entsprechenden Informationen gefüllt wird.  Wie diese Informationen interpretiert werden, hängt von der Art des Symbols und diese Informationen auch für ab.  Ausführliche Informationen finden Sie unter [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md).  
  
## Siehe auch  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)