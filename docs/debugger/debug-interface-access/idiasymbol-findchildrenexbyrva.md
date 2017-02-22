---
title: "IDiaSymbol::findChildrenExByRVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByRVA"
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die untergeordneten Elemente des Symbols ab, die an einer angegebenen relativen virtuellen Adresse \(RVA\) gültig sind.  
  
## Syntax  
  
```cpp#  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `symtag`  
 \[in\]  Gibt die Symbol Tags der abzurufenden untergeordneten Elemente an, wie in [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)definiert.  Auf `SymTagNull` , sodass alle untergeordneten Elemente abgerufen werden können.  
  
 `name`  
 \[in\]  Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen.  Auf `NULL` , sodass alle untergeordneten Elemente abgerufen werden können.  
  
 `compareFlags`  
 \[in\]  Gibt die Vergleichsoptionen an angewendet werden, um Übereinstimmungen zu benennen.  Werte aus der [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)\-Enumeration können allein oder in Kombination verwendet werden.  
  
 `address`  
 \[in\]  Gibt die RVA an.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)\-Objekt zurück, das eine Liste der untergeordneten abgerufenen Symbole enthält.  
  
## Rückgabewert  
 Gibt `S_OK` , wenn mindestens ein untergeordnetes Element des Symbols gefunden wurde, oder `S_FALSE` zurück, wenn keine untergeordneten Elemente gefunden wurden. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die lokalen Symbole, die Informationen über den Bereich Live zurückgegebene Zu sind.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)