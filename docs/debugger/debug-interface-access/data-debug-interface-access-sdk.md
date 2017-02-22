---
title: "Daten (Debug Interface Access SDK) | Microsoft Docs"
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
  - "Globale Variablen [C++], als Symbole"
  - "Lokale Variablen [C++], als Symbole"
  - "Klassenmember [C++], als Symbole"
  - "Datensymbol"
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Daten (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Alle Variablen, wie Parameter, lokale Variablen, globale Variablen und Klassenmember, werden von `SymTagData` Symbole bezeichnet.  Konstante Werte \(`LocIsConstant`\) werden ebenfalls mit diesem Typ bezeichnet.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Wenn ein Feld, einen der Werte [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset der Position. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Abschnitts teil Speicherort. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` ,  wenn die diese Adresse der Daten durch ein anderes Symbol verwiesen wird.|  
|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Bitposition der Position. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) nicht unterstützt \(DIA SDK v8.0\).|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol für die Klasse, wenn dies eine Struktur, Union oder ein Klassenfeld ist.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID des Symbols des Klassen übergeordnete Elemente übergeordneten Elements.|  
|[IDiaSymbol::get\_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` ,  wenn die Daten vom Compiler generiert wurden.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` ,  wenn die Daten als konstant gekennzeichnet ist.|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Einer der [DataKind\-Enumeration](../../debugger/debug-interface-access/datakind.md)\-Werte.|  
|[IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` ,  wenn die Daten als Teil eines aggregierten Datentyps ist nur im SDK \(DIA v8.0 und höher\).|  
|[IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` , wenn Daten ist, ist in ein Aggregat mehrerer Symbole geteilt wurden \(DIA nur im SDK v8.0 und höher\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Länge Bitfeld. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Kompiliereinheit, die Funktion oder den Block.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Jede der zulässigen Typen Speicherort. Ausführliche Informationen finden Sie unter [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Name der Variablen.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Entsprechung für den Inhalt der Register aus. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Registriert kennzeichner des Speicherorts. Ausführliche Informationen finden Sie unter [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position der Daten innerhalb des Blocks.|  
|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Ruft Slotnummer der Daten ab.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagData` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Das Metadatentoken, das die Daten darstellt.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol für den Variablentyp.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID des Symbols für das Variablentyp.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ,  wenn die Daten nicht ausgerichtet ist.|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Der Wert der konstanten Daten.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position der Daten in der ausführbaren Datei.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ,  wenn die Daten als flüchtig gekennzeichnet ist.|  
  
## Siehe auch  
 [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)   
 [DataKind\-Enumeration](../../debugger/debug-interface-access/datakind.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)