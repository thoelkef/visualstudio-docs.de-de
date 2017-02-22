---
title: "IDiaEnumSymbolsByAddr::Next | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSymbolsByAddr::Next-Methode"
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die folgenden Symbole in der Reihenfolge Adresse ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der Symbole im Enumerator abgerufen werden sollen.  
  
 rgelt  
 \[out\]  Ein Array, das dem [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt gefüllt werden soll, die die gewünschten Symbole darstellen.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl der Symbole im abgerufenen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Symbole vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Mit dieser Methode wird die Position der Enumerator durch die Anzahl der abgerufenen Elemente.  
  
## Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)