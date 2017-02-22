---
title: "Lexikalische Hierarchie der Symboltypen | Microsoft Docs"
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
  - "Symbole [DIA-SDK], Typhierarchien"
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Lexikalische Hierarchie der Symboltypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der folgenden Tabelle werden die Typen von Symbol in die lexikalische Hierarchie an.  
  
## Symbol\-Typen  
  
|Symbol "|Beschreibung|  
|--------------|------------------|  
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Gibt einen Speicherort mit Anmerkungen im Programmcode an.|  
|[Block](../../debugger/debug-interface-access/block.md)|Gibt geschachtelte Bereiche in den Funktionen.|  
|`Compiland`|Gibt `compiland` an, das der EXE\-Datei verknüpft ist.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt Kompiliereinheits Daten an, die weitere Details zur Kompiliereinheits laden und somit die mehraufwand verursachen, der abgerufen werden soll.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt alle zusätzlichen Umgebungsvariablen an, die zur Kompilierung der Kompiliereinheit von Bedeutung sind.|  
|[Benutzerdefiniert \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|  
|[Daten \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt diese Variablen als Parameter, lokale Variablen, globale Variablen und Klassenmember an.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt den globalen Bereich der Daten an. entspricht einem gesamten EXE\- oder DLL\-Datei.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt eine Funktion an, die einen definierten Punkt, an dem Debuggen beendet ist.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt eine Funktion an, die einen definierten Punkt, an dem Debuggen beginnen soll.|  
|[Funktion \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion an.|  
|[Label \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode an.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol an, das angezeigt wird, wenn das ausführbare Programm erstellt.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt `thunk`an.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt einen `namespace`Bezeichner an.|  
  
> [!NOTE]
>  Zusätzliche Symbol Eigenschaften können je nach dem Typ des Symbols verfügbar.  Diese Eigenschaften werden in den einzelnen Themen Symbole aufgelistet.  
  
## Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)