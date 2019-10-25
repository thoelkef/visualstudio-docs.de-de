---
title: SymTagEnum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738515"
---
# <a name="symtagenum"></a>SymTagEnum
Gibt den Typ des Symbols an.

## <a name="syntax"></a>Syntax

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Elements
`SymTagNull` gibt an, dass das Symbol keinen Typ aufweist.

`SymTagExe` gibt an, dass das Symbol eine exe-Datei ist. Es gibt nur ein `SymTagExe` Symbol pro Symbol Speicher. Er fungiert als globaler Bereich und verfügt über kein lexikalisches übergeordnetes Element.

`SymTagCompiland` gibt das compilersymbol für jede Compilerkomponente des Symbol Speicher an. Bei nativen Anwendungen entsprechen `SymTagCompiland` Symbole den Objektdateien, die mit dem Bild verknüpft sind. Für einige Arten von Microsoft Intermediate Language (MSIL)-Images gibt es eine compilerklasse pro Klasse.

`SymTagCompilandDetails` gibt an, dass das Symbol Erweiterte Attribute von compiland enthält. Das Abrufen dieser Eigenschaften erfordert möglicherweise das Laden von compilund Symbolen.

`SymTagCompilandEnv` gibt an, dass das Symbol eine Umgebungs Zeichenfolge ist, die für den kompiand definiert ist.

`SymTagFunction` gibt an, dass das Symbol eine Funktion ist.

`SymTagBlock` gibt an, dass das Symbol ein Block ist.

`SymTagData` gibt an, dass das Symbol Daten ist.

`SymTagAnnotation` gibt an, dass das Symbol für eine Code Anmerkung ist. Untergeordnete Elemente dieses Symbols sind konstante Daten Zeichenfolgen (`SymTagData`, `LocIsConstant` `DataIsConstant`). Diese Symbole werden von den meisten Clients ignoriert.

`SymTagLabel` gibt an, dass das Symbol eine Bezeichnung ist.

`SymTagPublicSymbol` gibt an, dass das Symbol ein öffentliches Symbol ist. Bei nativen Anwendungen ist dieses Symbol das externe COFF-Symbol, das beim Verknüpfen des Bilds aufgetreten ist.

`SymTagUDT` gibt an, dass das Symbol ein benutzerdefinierter Typ (Struktur, Klasse oder Union) ist.

`SymTagEnum` gibt an, dass das Symbol eine Enumeration ist.

`SymTagFunctionType` gibt an, dass das Symbol ein Funktions Signatur Typen ist.

`SymTagPointerType` gibt an, dass das Symbol ein Zeigertyp ist.

`SymTagArrayType` gibt an, dass das Symbol ein Arraytyp ist.

`SymTagBaseType` gibt an, dass das Symbol ein Basistyp ist.

`SymTagTypedef` gibt an, dass das Symbol ein `typedef` ist, d. h. ein Alias für einen anderen Typ.

`SymTagBaseClass` gibt an, dass das Symbol eine Basisklasse eines benutzerdefinierten Typs ist.

`SymTagFriend` gibt an, dass das Symbol ein Freund eines benutzerdefinierten Typs ist.

`SymTagFunctionArgType` gibt an, dass das Symbol ein Funktions Argument ist.

`SymTagFuncDebugStart` gibt an, dass das Symbol die Endposition des prologcodes der Funktion ist.

`SymTagFuncDebugEnd` gibt an, dass das Symbol die Anfangsposition des epilogcodes der Funktion ist.

`SymTagUsingNamespace` gibt an, dass das Symbol ein Namespace Name ist, der im aktuellen Bereich aktiv ist.

`SymTagVTableShape` gibt an, dass das Symbol eine virtuelle Tabellen Beschreibung ist.

`SymTagVTable` gibt an, dass das Symbol ein virtueller Tabellen Zeiger ist.

`SymTagCustom` gibt an, dass das Symbol ein benutzerdefiniertes Symbol ist und nicht von Dia interpretiert wird.

`SymTagThunk` gibt an, dass das Symbol ein Thunk ist, der zum Freigeben von Daten zwischen 16 und 32 Bit-Code verwendet wird.

`SymTagCustomType` gibt an, dass das Symbol ein benutzerdefiniertes compilersymbol ist.

`SymTagManagedType` gibt an, dass das Symbol in den Metadaten angegeben ist.

`SymTagDimension` gibt an, dass das Symbol ein mehrdimensionales Fortran-Array ist.

`SymTagCallSite` gibt an, dass das Symbol die CallSite darstellt.

`SymTagInlineSite` gibt an, dass das Symbol die Inline Site darstellt.

`SymTagBaseInterface` gibt an, dass das Symbol eine Basisschnittstelle ist.

`SymTagVectorType` gibt an, dass das Symbol ein Vector-Typ ist.

`SymTagMatrixType` gibt an, dass das Symbol ein Matrix-Typ ist.

`SymTagHLSLType` gibt an, dass das Symbol ein allgemeiner Shader-Sprachtyp ist.

## <a name="remarks"></a>Hinweise
Alle Symbole in einer Debugdatei verfügen über ein identifizierendes Tag, das den Typ des Symbols angibt.

Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -Methode zurückgegeben.

Die Werte in dieser Enumeration werden an die folgenden Methoden übermittelt, um den Suchbereich auf einen bestimmten Symboltyp zu begrenzen:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
