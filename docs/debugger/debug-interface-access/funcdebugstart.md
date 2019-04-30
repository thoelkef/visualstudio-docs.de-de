---
title: FuncDebugStart | Microsoft-Dokumentation
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
ms.openlocfilehash: 078c2b7bfcf6ce2a86b5f059053f8f31376af595
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554530"
---
# <a name="funcdebugstart"></a>FuncDebugStart
Verfügt eine Funktion definierten Punkt mit dem Debuggen begonnen werden soll, dass ein Symbol mit Punkt identifiziert ist eine `SymTagFuncDebugStart` Tag.

## <a name="properties"></a>Eigenschaften
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.

|Eigenschaft|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Zeitzonenoffset-Teil des Speicherorts; Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Abschnitt daran des Speicherorts. Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Wenn die Funktion eine benutzerdefinierte Aufrufkonvention (nur in DIA-SDK-Version 8.0 oder höher) verwendet.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Wenn die Funktion eine weit zurück (nur in DIA-SDK-Version 8.0 oder höher) führt.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Wenn die Funktion eine Rückgabe von Interrupt (nur in DIA-SDK-Version 8.0 oder höher) enthält.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Wenn die Funktion als statische (nur in DIA-SDK-Version 8.0 oder höher) markiert ist.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Funktion.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Anfangs-haben statische Speicherorte; Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Wenn die Funktion angegeben wurde, mit der [Noinline](/cpp/cpp/noinline) Attribut (nur in DIA-SDK-Version 8.0 oder höher).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Wenn die Funktion angegeben wurde, mit der [Noreturn](/cpp/cpp/noreturn) Attribut (nur in DIA-SDK-Version 8.0 oder höher).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Wenn die Funktion nie (nur in DIA-SDK-Version 8.0 oder höher) aufgerufen wird.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset des Symbols im Speicher; Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Wenn der Code die Debuginformationen für optimierten Code (nur in DIA-SDK-Version 8.0 oder höher) aufweist.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position der Funktion innerhalb des Blocks.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFuncDebugStart` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Die Position der Funktion in der ausführbaren Datei.|

## <a name="see-also"></a>Siehe auch
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)
- [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)