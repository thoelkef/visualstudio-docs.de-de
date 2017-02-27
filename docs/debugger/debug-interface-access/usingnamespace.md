---
title: "UsingNameSpace | Microsoft Docs"
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
  - "UsingNamespace-Symboltag"
ms.assetid: e8e1beb5-7cb9-43b4-9ff4-760d5f91ea2d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# UsingNameSpace
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Einige Symbole können durch Namespace und würden anschließend die durch ein `SymTagUsingNameSpace`\-Tag angegeben werden.  
  
> [!NOTE]
>  Das UsingNamespace\-Symbol tag wird nur in verwaltetem Code.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Kompiliereinheit, den Block oder Funktion.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Namespacename.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagNameSpace` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Siehe auch  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)