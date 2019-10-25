---
title: Lexikalische Hierarchie von Symbol Typen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad782ddb9a88b492d03e2338f17d95fb7bfa4f79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738674"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikalische Hierarchie der Symboltypen
In der folgenden Tabelle werden die Symboltypen in der lexikalischen Hierarchie angezeigt.

## <a name="symbol-types"></a>Symbol Typen

|Symboltyp|Beschreibung|
|-----------------|-----------------|
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Gibt eine mit Anmerkungen versehene Position im Programmcode an.|
|[Block](../../debugger/debug-interface-access/block.md)|Gibt die in Funktionen unter fallenen Bereiche an.|
|`Compiland`|Gibt eine `compiland` an, die mit der exe-Datei verknüpft ist.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt Kompilierungen und Daten an, für die möglicherweise zusätzliche compilerdetails geladen werden müssen, sodass der abzurufende Lauf Zeitaufwand entsteht.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt alle zusätzlichen Umgebungsvariablen an, die für die Kompilierung des Kompilierens wichtig sind.|
|[Benutzerdefiniert (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|
|[Daten (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt Variablen wie Parameter, lokale Variablen, globale Variablen und Klassenmember an.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt den globalen Gültigkeitsbereich der Daten an. entspricht einer vollständigen exe-oder DLL-Datei.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt eine Funktion an, die über einen definierten Punkt verfügt, an dem das Debuggen beendet werden soll.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt eine Funktion an, die über einen definierten Punkt verfügt, an dem der Debugvorgang beginnen soll.|
|[Funktion (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion an.|
|[Label (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode an.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol an, das angezeigt wird, wenn das ausführbare Programm aufgebaut wird.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt eine `thunk` an.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt eine `namespace`identifier an.|

> [!NOTE]
> Je nach Symboltyp sind möglicherweise weitere Symbol Eigenschaften verfügbar. Diese Eigenschaften sind in den einzelnen Symbolthemen aufgeführt.

## <a name="see-also"></a>Siehe auch
- [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)