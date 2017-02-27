---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren-Methode"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die untergeordneten Elemente des Symbols ab.  
  
## Syntax  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `symtag`  
 \[in\]  Gibt die Symbol Tags der abzurufenden untergeordneten Elemente an, wie in [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)definiert.  Auf `SymTagNull` , sodass alle untergeordneten Elemente abgerufen werden können.  
  
 `name`  
 \[in\]  Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen.  Auf `NULL` , sodass alle untergeordneten Elemente abgerufen werden können.  
  
 `compareFlags`  
 \[in\]  Gibt die Vergleichsoptionen, die angewendet werden, um Übereinstimmungen zu benennen.  Werte aus der [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)\-Enumeration können allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)\-Objekt zurück, das eine Liste der untergeordneten abgerufenen Symbole enthält.  
  
## Rückgabewert  
 Gibt `S_OK` , wenn mindestens ein untergeordnetes Element des Symbols gefunden wurde, oder `S_FALSE` zurück, wenn keine untergeordneten Elemente gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Diese Methode entspricht dem Aufrufen der Methode mit diesem Symbol [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) als erster Parameter identisch.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)