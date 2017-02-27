---
title: "IDiaEnumSymbols::Next | Microsoft Docs"
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
  - "IDiaEnumSymbols::Next-Methode"
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Symbolen in der Enumerationsfolge ab.  
  
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
 \[out\]  Ein Array, das den [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekten gefüllt werden soll, die die gewünschten Symbole darstellen.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl der Symbole im abgerufenen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Symbole vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
  
```cpp#  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## Siehe auch  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)