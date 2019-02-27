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
ms.openlocfilehash: dbc86bb43048b06bc1f7080bc6cb579771138c49
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607745"
---
# <a name="symtagenum"></a>SymTagEnum
Gibt den Typ des Symbols.

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
`SymTagNull` Gibt an, dass das Symbol keinen Typ hat.

`SymTagExe` Gibt an, dass das Symbol eine .exe-Datei ist. Es gibt nur ein `SymTagExe` Symbol pro Symbolspeicher. Es dient als dem globalen Bereich und keine lexikalische ein übergeordnetes Element.

`SymTagCompiland` Gibt die Compiland-Symbol für jede Komponente Kompiliereinheit des Symbolspeichers an. Für native Anwendungen `SymTagCompiland` Symbole entsprechen die Objektdateien verknüpft werden, in dem Abbild. Für einige Arten von Images von Microsoft Intermediate Language (MSIL) gibt es eine Kompiliereinheit pro Klasse.

`SymTagCompilandDetails` Gibt an, dass das Symbol erweiterten Attribute von der Kompiliereinheit enthält. Abrufen der folgenden Eigenschaften unter Umständen Compiland-Symbole werden geladen.

`SymTagCompilandEnv` Gibt an, dass das Symbol einer Umgebungszeichenfolge für der Kompiliereinheit definiert ist.

`SymTagFunction` Gibt an, dass das Symbol eine Funktion.

`SymTagBlock` Gibt an, dass das Symbol mit einem geschachtelten Block ist.

`SymTagData` Gibt an, dass das Symbol Daten.

`SymTagAnnotation` Gibt an, dass das Symbol für einen Code-Anmerkung. Untergeordnete Elemente dieses Symbol sind Konstante Zeichenfolgen (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Die meisten Clients ignorieren Sie dieses Symbol.

`SymTagLabel` Gibt an, dass das Symbol eine Bezeichnung ist.

`SymTagPublicSymbol` Gibt an, dass das Symbol ein public-Symbol. Für native Anwendungen ist dieses Symbol das externe COFF-Symbol verknüpfen das Image aufgetreten.

`SymTagUDT` Gibt an, dass das Symbol mit einem benutzerdefinierten Typ (Struktur, Klasse oder Union) ist.

`SymTagEnum` Gibt an, dass das Symbol eine Enumeration ist.

`SymTagFunctionType` Gibt an, dass das Symbol ein Signatur Funktionstyp ist.

`SymTagPointerType` Gibt an, dass das Symbol ein Zeigertyp ist.

`SymTagArrayType` Gibt an, dass das Symbol ein Arraytyp ist.

`SymTagBaseType` Gibt an, dass das Symbol ein Basistyp ist.

`SymTagTypedef` Gibt an, dass das Symbol ist ein `typedef`, d.h. ein Alias für einen anderen Typ.

`SymTagBaseClass` Gibt an, dass das Symbol eine Basisklasse eines benutzerdefinierten Typs ist.

`SymTagFriend` Gibt an, dass das Symbol mit einem Freund eines benutzerdefinierten Typs ist.

`SymTagFunctionArgType` Gibt an, dass das Symbol ein Funktionsargument ist.

`SymTagFuncDebugStart` Gibt an, dass das Symbol, das die Position am Ende der Funktionsprologcode ist.

`SymTagFuncDebugEnd` Gibt an, dass das Symbol die Anfangsposition des epilogcodes der Funktion ist.

`SymTagUsingNamespace` Gibt an, dass das Symbol ein Namespacename, der im aktuellen Bereich aktiv ist.

`SymTagVTableShape` Gibt an, dass das Symbol eine Beschreibung der virtuellen Tabelle ist.

`SymTagVTable` Gibt an, dass das Symbol eine virtuelle Tabelle-Zeiger ist.

`SymTagCustom` Gibt an, dass das Symbol ein benutzerdefiniertes Symbol ist, und nicht durch von Dia interpretiert

`SymTagThunk` Gibt an, dass das Symbol ein Thunk für die Freigabe von Daten zwischen 16 und 32-Bit-Code verwendet wird.

`SymTagCustomType` Gibt an, dass das Symbol ein benutzerdefinierter Compiler-Symbol.

`SymTagManagedType` Gibt an, dass das Symbol in den Metadaten ist.

`SymTagDimension` Gibt an, dass das Symbol ein FORTRAN mehrdimensionales Array ist.

`SymTagCallSite` Gibt an, dass das Symbol der aufrufenden Site darstellt.

`SymTagInlineSite` Gibt an, dass das Symbol die Inline-Website darstellt.

`SymTagBaseInterface` Gibt an, dass das Symbol eine Basisschnittstelle.

`SymTagVectorType` Gibt an, dass das Symbol ein vektortyp ist.

`SymTagMatrixType` Gibt an, dass das Symbol einen Matrixtyp ist.

`SymTagHLSLType` Gibt an, dass das Symbol ein High Level Shader Language-Typ ist.

## <a name="remarks"></a>Anmerkungen
Alle Symbole in einer Debugdatei haben ein Identifizierungstag, der das Symbol für den Typ angibt.

Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) Methode.

Die Werte in dieser Enumeration werden für die folgenden Methoden zum Begrenzen des Bereichs der Suche auf einen bestimmten Symboltyp übergeben:

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
