---
title: "IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs"
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
  - "IDiaSymbol::get_localBasePointerRegisterId-Methode"
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDiaSymbol::get_localBasePointerRegisterId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die ID des Registers ab, das einen niedrigen Zeiger auf lokale Variablen auf dem Stapel abgelegt sind.  Verwenden Sie diese Option, wenn [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) zu `SymTagFunction`festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_localBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die ID des Registers zurück, das einen niedrigen Zeiger auf lokale Variablen auf dem Stapel abgelegt sind.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)