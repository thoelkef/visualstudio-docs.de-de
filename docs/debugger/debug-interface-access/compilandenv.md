---
title: "CompilandEnv | Microsoft Docs"
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
  - "CompilandEnv-Symbol"
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# CompilandEnv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Compiler schließt möglicherweise zusätzliche Umgebungsvariablen mit Symbolen ein.  Es gibt ein `SymTagCompilandEnv` Symbol für jede dieser Variablen.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für Elemente Kompiliereinheit.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Name der Variablen.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandEnv` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|STRING\-bewertete Inhalt der Variablen \(`VT_BSTR`\).|  
  
## Siehe auch  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)