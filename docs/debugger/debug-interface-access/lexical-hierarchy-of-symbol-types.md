---
title: Lexikalische Hierarchie der Symboltypen | Microsoft-Dokumentation
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
ms.openlocfilehash: f4b2e6fc0b24cc96f617e7b78c6bdcc59ddc5c0d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399400"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikalische Hierarchie der Symboltypen
Die folgende Tabelle zeigt die Symboltypen in der lexikalische Hierarchie an.

## <a name="symbol-types"></a>Symboltypen

|Symboltyp|Beschreibung|
|-----------------|-----------------|
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Hiermit wird ein mit Anmerkungen versehenen Speicherort im Programmcode.|
|[Block](../../debugger/debug-interface-access/block.md)|Gibt geschachtelte Bereiche in Funktionen an.|
|`Compiland`|Gibt an, eine `compiland` zur .exe-Datei verknüpft.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt an, in denen möglicherweise zusätzliche Compiland-Details werden geladen und fallen daher die Laufzeit-overhead zum Abrufen von Compiland-Daten.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt zusätzliche Umgebungsvariablen für die Kompilierung von der Kompiliereinheit signifikant.|
|[Benutzerdefiniert (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|
|[Daten (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt die Variablen als Parameter, lokale Variablen, globale Variablen und Klassenmember an.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt den globalen Bereich der Daten an. entspricht einer vollständigen .exe oder .dll-Datei.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt an, eine Funktion mit einem bestimmten Zeitpunkt auf dem Debuggen besteht darin, zu beenden.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt an, eine Funktion mit einem bestimmten Zeitpunkt unter dem Debuggen begonnen werden soll.|
|[Funktion (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion.|
|[Label (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol, das angezeigt wird, wenn Sie das ausführbare Programm zu erstellen.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt an, eine `thunk`.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt an, eine `namespace`Bezeichner.|

> [!NOTE]
> Zusätzliche Symboleigenschaften können je nach den Symboltyp verfügbar sein. Diese Eigenschaften werden in den einzelnen Symbol-Themen aufgelistet.

## <a name="see-also"></a>Siehe auch
- [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)