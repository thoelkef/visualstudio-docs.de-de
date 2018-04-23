---
title: Lexikalische Hierarchie der Symboltypen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58c4ef49cb7eabae7608ce417e4f3d5ef99a8284
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikalische Hierarchie der Symboltypen
In der folgenden Tabelle zeigt die Symboltypen in der lexikalische Hierarchie an.  
  
## <a name="symbol-types"></a>Symboltypen  
  
|Symboltyp|Beschreibung|  
|-----------------|-----------------|  
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Gibt einen mit Anmerkungen versehenen Speicherort im Programmcode.|  
|[Block](../../debugger/debug-interface-access/block.md)|Gibt geschachtelte Bereiche in Funktionen an.|  
|`Compiland`|Gibt eine `compiland` zur .exe-Datei verknüpft.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt an, in denen möglicherweise zusätzliche Kompiliereinheit Details werden geladen und fallen daher zum Abrufen von Laufzeit-overhead Kompiliereinheit-Daten.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt zusätzliche Umgebungsvariablen für die Kompilierung von der Kompiliereinheit signifikant.|  
|[Benutzerdefiniert (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|  
|[Daten (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt die Variablen als Parameter, lokale Variablen, globale Variablen und Klassenmember an.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt die globalen Bereich der Daten an. entspricht einer vollständigen .exe oder .dll-Datei.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt eine Funktion mit einem bestimmten Zeitpunkt an, an welche Debuggen wird beendet.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt eine Funktion mit einem bestimmten Zeitpunkt an, an welche Debuggen begonnen werden soll.|  
|[Funktion (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion.|  
|[Label (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol, das angezeigt wird, wenn das ausführbare Programm zu erstellen.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt eine `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt eine `namespace`Bezeichner.|  
  
> [!NOTE]
>  Zusätzliche Symboleigenschaften können je nach der Symboltyp verfügbar sein. Diese Eigenschaften werden in den einzelnen Symbol Themen aufgelistet.  
  
## <a name="see-also"></a>Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)