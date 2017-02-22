---
title: "IDiaSymbol::get_unmodifiedType | Microsoft Docs"
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
  - "IDiaSymbol::get_unmodifiedType-Methode"
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_unmodifiedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den ursprünglichen Datentyp für dieses Symbol ab.  Verwenden Sie diese Option, wenn [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) auf einen Typ festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das den ursprünglichen Typ dieses Symbols darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Der aktuelle Typ ist eine Änderung des zurückgegebenen ursprünglichen Typs.  Der ursprüngliche Typ für ein Symbol kann bestimmt werden, indem zuerst den Typ des Symbols abgerufen und dann das zurückgegebener Typ für den ursprünglichen Typ verhört.  Beachten Sie, dass einige Symbole möglicherweise keinen geänderten Typ ursprüngliche Typ aufweisen.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)