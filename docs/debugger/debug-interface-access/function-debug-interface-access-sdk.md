---
title: Function (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd901d1bb54f91042e0a8134f1f3cba6c29b396a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745128"
---
# <a name="function-debug-interface-access-sdk"></a>Funktion (Debug Interface Access SDK)
Jede Funktion wird durch ein `SymTagFunction` Symbol gekennzeichnet.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.

|property|`Data type`|Beschreibung|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Einer der Werte der CV_access_e- [Enumeration](../../debugger/debug-interface-access/cv-access-e.md), wenn die Funktion eine Member-Funktion ist.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Das Symbol für die-Klasse, wenn die Funktion eine Member-Funktion ist.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID des übergeordneten Symbols der Klasse.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, wenn die Funktion als Konstante markiert ist.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`, wenn die Funktion eine benutzerdefinierte Aufruf Konvention verwendet (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`, wenn die Funktion eine lange Rückgabe ausführt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE`, wenn die Funktion eine zugeordnete Arbeitsspeicher Funktion verwendet (nur uinnder Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE`, wenn die Funktion C++eine Ausnahmebehandlung im Stil enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE`, wenn die Funktion eine asynchrone Ausnahmebehandlung enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE`, wenn die Funktion eine Inlineassembly enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE`, wenn die Funktion einen [longjmp](/cpp/c-runtime-library/reference/longjmp) -Befehl enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`, wenn die Funktion Sicherheitsüberprüfungen enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE`, wenn die Funktion eine strukturierte Ausnahmebehandlung im Win32-Stil enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE`, wenn die Funktion einen [setjmp](/cpp/c-runtime-library/reference/setjmp) --Befehl enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`, wenn die Funktion eine Rückgabe von Interrupt hat (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE`, wenn eine Funktion ein virtuelles Intro ist.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE`, wenn die Funktion mit einem der [Inline-, __inline-\__forceinline](/cpp/cpp/inline-functions-cpp) Attribute gekennzeichnet wurde.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE`, wenn die Funktion mit dem [Naked](/cpp/cpp/naked-cpp) -Attribut markiert ist (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`, wenn die Funktion statisch ist (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Anzahl von Bytes an Funktionscode, beginnend mit dem Speicherort.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol der einschließenden Kompilierungen.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Funktionen können statische oder Metadatenspeicher Orte aufweisen. Weitere Informationen finden Sie unter [Symbol Speicherorte](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Name der Funktion.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`, wenn es sich bei der Funktion nicht um eine Inline Funktion handelt (nur n Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`, wenn die Funktion nicht erreichbar ist (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`, wenn die Funktion keinen Wert zurückgibt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE`, wenn die Funktion mit Puffer Sicherheitsüberprüfungen kompiliert wurde, aber keine Stapel Anordnung durchgeführt werden konnte.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`, wenn der Code über Debuginformationen für optimierten Code verfügt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE`, wenn die Funktion rein virtuell ist.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position dieser Funktion innerhalb Ihres Moduls.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFunction` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Metadatentoken für die Funktion.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol für die Funktions Signatur.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID des typsymbols.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, wenn die Funktion nicht ausgerichtet ist.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Die nicht ergänzte Form des Funktionsnamens (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Teil oder vollständig der nicht ergänzten Form des Funktionsnamens (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`, wenn eine virtuelle Funktion ist.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position dieser Funktion innerhalb des ausführbaren Bilds.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Wenn eine virtuelle Funktion ist, dann der Offset in der virtuellen Funktions Tabelle.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, wenn die Funktion als flüchtig markiert ist.|

## <a name="see-also"></a>Siehe auch
- [CV_access_e-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)
- [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)