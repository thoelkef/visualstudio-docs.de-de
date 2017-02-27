---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev-Methode"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die vorherige Symbole in der Reihenfolge Adresse ab.  
  
## Syntax  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der Symbole im Enumerator abgerufen werden sollen.  
  
 rgelt  
 \[out\]  Ein Array, das [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekten gefüllt werden soll, die die gewünschten Symbole darstellen.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl der Symbole im abgerufenen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine vorherigen Symbole vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Mit dieser Methode wird die Position der Enumerator durch die Anzahl der abgerufenen Elemente.  
  
## Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)