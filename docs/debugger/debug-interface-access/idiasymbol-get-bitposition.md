---
title: "IDiaSymbol::get_bitPosition | Microsoft Docs"
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
  - "IDiaSymbol::get_bitPosition-Methode"
ms.assetid: b0059407-8655-497b-81ca-025595989371
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_bitPosition
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Bitposition der Position ab.  Wird verwendet, wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)`LocIsBitField`ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_bitPosition (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Bitposition der Position zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)