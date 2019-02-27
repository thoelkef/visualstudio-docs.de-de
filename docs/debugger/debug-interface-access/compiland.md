---
title: Compiland | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecdd4284e4c7c417af6ebd935418d56cf601bb74
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613241"
---
# <a name="compiland"></a>Compiland
Es gibt ein `SymTagCompiland` symbol für jede Kompiliereinheit zur .exe-Datei verknüpft. Kompiliereinheit Informationen Symbole mit aufgeteilt ist eine `SymTagCompiland` -Tag, das abgerufen werden kann, ohne zusätzliche Compiland-Symbole werden geladen und Symbole mit einer `SymTagCompilandDetails` -Tag, das möglicherweise zusätzliche Symbole werden geladen.

## <a name="properties"></a>Eigenschaften
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.

|Eigenschaft|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Wenn bei der Kompilierung bearbeiten und Fortfahren aktiviert wurde.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die .exe-Datei.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|Der Name der Bibliothek oder Objektdatei-Datei, in dem Objekt geladen wurde.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Dateiname der Kompiliereinheit der Objektdatei.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|Der Name der Quelldatei.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompiland` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|

## <a name="see-also"></a>Siehe auch
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
- [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)