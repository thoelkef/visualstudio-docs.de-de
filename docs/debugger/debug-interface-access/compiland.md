---
title: "Compiland | Microsoft Docs"
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
  - "Compiland-Symbol"
  - "Compilands, Compiland-Symbol"
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt ein `SymTagCompiland` Symbol für jede Kompiliereinheit, die der EXE\-Datei verknüpft ist.  Informationen Kompiliereinheits werden zwischen Symbole mit einem `SymTagCompiland`\-Tag, das abgerufen werden kann, ohne dass zusätzliche Symbole zu laden, und Kompiliereinheits Symbole mit einem `SymTagCompilandDetails`\-Tag geteilt, das möglicherweise zusätzliche das Laden von Symbolen erfordert.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|Bearbeiten und Fortfahren`TRUE` ,  wenn bei der Kompilierung aktiviert wurden.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die EXE\-Datei.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|Der Name der Bibliothek oder Objektdatei mit der Objekt geladen wurde.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Dateiname der Objektdatei der Kompiliereinheit.|  
|[IDiaSymbol::get\_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|Name der Quelldatei.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompiland` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Siehe auch  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)