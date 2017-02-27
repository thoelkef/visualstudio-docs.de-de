---
title: "Thunk | Microsoft Docs"
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
  - "Thunk-Eigenschaften [DIA-SDK]"
  - "Thunk-Symbol"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Thunk
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Jedes `thunk` wird durch ein `SymTagThunk`\-Tag identifiziert.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Zugriffsmodifizierer Attribut für, einer der [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md) nur Werte \(DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Entsprechung für einen Teil Speicherort aus. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Abschnitts teil Speicherort. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Einschließende Klasse\-übergeordnetes übergeordnet \(ggf. nur unter V8.0 DIA SDK oder höher\).|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID des übergeordneten Symbols der einschließenden Klasse nur \(DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|TRUE, wenn der Thunk als Konstante gekennzeichnet ist \(nur DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|TRUE, wenn der Thunk eine Einführung in einer virtuellen Funktion ist nur in V8.0 DIA SDK \(oder höher\)|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|TRUE, wenn der Thunk als statisch gilt nur \(DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Anzahl von Bytes des Codes im Thunk.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Kompiliereinheit, den Block oder Funktion.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Endpunkte haben statischen Speicherort. Ausführliche Informationen finden Sie unter [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)\-Enumeration.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Name des Thunks.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|TRUE, wenn der Thunk rein virtuelle ist \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position des Thunks innerhalb des Moduls.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagThunk` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Offset der Position des Thunk ziels.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Relative virtuelle Adresse des Thunk ziels in einem einschließenden Block.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Abschnitts des Thunk ziels.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Position des Thunk ziels im ausführbaren Bild.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Thunk den Typ, wie von [THUNK\_ORDINAL\-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)definiert.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Der Typ des Thunks \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID des Symbols für das Typ nur \(DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ,  wenn der Thunk nicht ausgerichtet wird \(nur DIA SDK in V8.0 oder höher\)|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` ,  wenn der Thunk virtuell ist \(nur DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position des Thunks innerhalb des ausführbaren Images.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Der Offset in der virtuellen Tabelle nur auf diesen Thunk \(DIA SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ,  wenn der Thunk als flüchtig gekennzeichnet ist \(nur DIA SDK in V8.0 oder höher\).|  
  
## Siehe auch  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK\_ORDINAL\-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)