---
title: "CustomType | Microsoft Docs"
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
  - "CustomType-Symbol"
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# CustomType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Anbieter\-definierte compilerspezifisch Typen \(Typen\) `SymTagCustomType` werden durch ein Symbol gekennzeichnet.  
  
## Eigenschaften  
 In der folgenden Tabelle sind die zusätzlichen gültige Eigenschaften für diesen Typ Symbol an.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|Bezeichner der OEM.|  
|[IDiaSymbol::get\_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|`DWORD`|Interne OEM ID.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCustomType` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Der erste Typ vom benutzerdefinierten Typ verwiesen wird.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID des Symbols für das Typ.|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|Array aller Arten von benutzerdefinierten Typ verwiesen wird.|  
  
## Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)