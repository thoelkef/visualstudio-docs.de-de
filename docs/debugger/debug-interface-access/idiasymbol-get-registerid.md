---
title: "IDiaSymbol::get_registerId | Microsoft Docs"
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
  - "IDiaSymbol::get_registerId-Methode"
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Registern kennzeichner des Speicherorts ab, wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) zu `LocIsEnregistered`festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Registern kennzeichner des Speicherorts zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Wenn das Symbol relativ zu einem Register entspricht. h. wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) des Symbols auf `LocIsRegRel`festgelegt ist, verwenden Sie die `get_registerId`\-Methode, die von einem Aufruf der [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)\-Methode folgt, um den Offset vom Registers abgerufen werden sollen, in dem das Symbol befindet.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)