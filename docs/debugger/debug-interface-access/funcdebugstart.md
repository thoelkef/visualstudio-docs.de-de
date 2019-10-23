---
title: Funcdebug-Start | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 339ee81dee59ae57e456fe0f38f1098783390259
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745156"
---
# <a name="funcdebugstart"></a>FuncDebugStart
Wenn eine Funktion über einen definierten Punkt verfügt, an dem das Debugging beginnen soll, wird dieser Punkt durch ein Symbol mit einem `SymTagFuncDebugStart`-Tag identifiziert.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.

|property|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`, wenn die Funktion eine benutzerdefinierte Aufruf Konvention verwendet (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`, wenn die Funktion eine lange Rückgabe durchführt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`, wenn die Funktion eine Rückgabe von Interrupt enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`, wenn die Funktion als statisch gekennzeichnet ist (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Das Symbol für die einschließende Funktion.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Start Punkte verfügen über statische Speicherorte. Weitere Informationen finden Sie unter [Symbol Speicherorte](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`, wenn die Funktion mit dem [noinline](/cpp/cpp/noinline) -Attribut angegeben wurde (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`, wenn die Funktion mit dem [noreturn](/cpp/cpp/noreturn) -Attribut angegeben wurde (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`, wenn die Funktion niemals aufgerufen wird (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset des Symbols im Speicher; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`, wenn der Code über Debuginformationen für optimierten Code verfügt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position der Funktion innerhalb des Blocks.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFuncDebugStart` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position der Funktion innerhalb der ausführbaren Datei.|

## <a name="see-also"></a>Siehe auch
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)
- [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)