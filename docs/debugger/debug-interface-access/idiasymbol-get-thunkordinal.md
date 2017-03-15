---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal-Methode"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Thunk den Typ einer Funktion ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [THUNK\_ORDINAL\-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)\-Enumeration zurück, die den Thunk den Typ der Funktion angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Diese Eigenschaft ist nur wenn das Symbol als [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Wert von `SymTagThunk`gültig.  
  
 Ein „Thunk“ ist ein Codeabschnitt, der zwischen einem 32\-Bit\-Speicheradressen \(auch als adressbereich flach Adressraum\) und einem 16\-Bit\-Adressraum konvertiert \(bekannt als segmentierter Adressraum\).  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK\_ORDINAL\-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)