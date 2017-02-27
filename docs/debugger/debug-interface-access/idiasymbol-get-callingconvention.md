---
title: "IDiaSymbol::get_callingConvention | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_callingConvention-Methode"
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_callingConvention
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt einen Indikator einer Methode aufrufkonvention zurück.  
  
## Syntax  
  
```cpp#  
HRESULT get_callingConvention (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [CV\_call\_e\-Enumeration](../../debugger/debug-interface-access/cv-call-e.md)\-Enumeration zurück, die die Aufrufkonvention der Methode angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_call\_e\-Enumeration](../../debugger/debug-interface-access/cv-call-e.md)