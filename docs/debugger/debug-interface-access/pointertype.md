---
title: "PointerType | Microsoft Docs"
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
  - "PointerType-Symbol"
ms.assetid: 67228681-7345-4537-8af3-93806803ee96
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# PointerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Jeder Zeiger wird durch ein `SymTagPointerType` Symbol identifiziert.  
  
## Eigenschaften  
 In der folgenden Tabelle sind die zusätzlichen gültige Eigenschaften für diesen Typ Symbol an.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` ,  wenn der Zeiger als Konstante gekennzeichnet ist.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Größe \(in Bytes\) des Zeigers.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol einschließenden [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE` ,  wenn der Zeiger ein Verweistyp ist.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagPointerType` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol für das Ziel des Zeigers.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID des Symbols für das Typ.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ,  wenn der Zeiger nicht ausgerichtet ist.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ,  wenn der Zeiger als flüchtig gekennzeichnet ist.|  
  
## Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)