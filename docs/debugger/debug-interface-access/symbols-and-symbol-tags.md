---
title: "Symbole und Symboltags | Microsoft Docs"
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
  - "Symbole [DIA-SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Symbole und Symboltags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debuginformationen über ein kompiliertes Programm werden in der Programmdatenbankdatei \(.pdb\) als Symbole gespeichert, die mithilfe des Schnittstellen\-Zugriffs Debuggen \(Durchmesser\) SDK API zugreifen kann.  Alle Symbole [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) und eine [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)\-Eigenschaft.  Die `symTag`\-Eigenschaft gibt die Art des Symbols an, wie durch die [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Enumeration definiert.  Die `symIndexId`\-Eigenschaft ist ein `DWORD`\-Wert, der den eindeutigen Bezeichner für jede Instanz eines Symbols enthält.  
  
 Symbole verfügen auch über die Eigenschaften, die zusätzliche Informationen über das Symbol als auch Verweise auf andere Symbole am häufigsten [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) oder [IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)angeben können.  Wenn Sie eine Eigenschaft abfragen, die den Verweis enthält, wird der Verweis als [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurückgegeben.  Diese Eigenschaften sind immer zugeordnet, mit einer anderen Eigenschaft mit dem gleichen Namen, jedoch mit „Id“, z. B. [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) und [IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)angefügt.  Die Tabellen in [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md), [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)und [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) Kontur die Eigenschaften für jede der verschiedenen Arten der Symbole.  Diese Eigenschaften verfügen möglicherweise über relevante Informationen oder Verweise auf andere Symbole.  Da die `*Id`\-Eigenschaften nur numerische ordinale Bezeichner ihrer zugehörigen Eigenschaften sind, werden sie von den anderen Diskussionen ausgelassen.  Sie werden lediglich für an welcher Stelle verwiesen erklärung Parameter.  
  
 Beim Versuch, die Eigenschaft zugreifen, wenn kein Fehler auftritt und die Symbole \- Eigenschaft ein Wert zugewiesen wurde, „get“ \- Methode zurückgibt `S_OK`der Eigenschaft ab.  Der Rückgabewert `S_FALSE` gibt an, dass die Eigenschaft für das aktuelle Symbol ungültig ist.  
  
## In diesem Abschnitt  
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)  
 Beschreibt die verschiedenen Arten von Speicherorten, die ein Symbol enthalten kann.  
  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Beschreibt die Typen von Symbolen, die lexikalische Hierarchien z. B. Dateien, Module und Funktionen bestehen.  
  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Beschreibt die Typen von Symbolen, die für unterschiedliche Sprachelemente wie Klassen, Arrays und Funktionen rückgabetypen entsprechen.  
  
## Siehe auch  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)