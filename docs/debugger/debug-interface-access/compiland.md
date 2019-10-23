---
title: Kompilieren | Microsoft-Dokumentation
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
ms.openlocfilehash: ccb4ca05374c86912cd48956262645b80fb14e40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745441"
---
# <a name="compiland"></a>Compiland
Es gibt ein `SymTagCompiland` Symbol für jede Kompilierungen, die mit der exe-Datei verknüpft ist. Compiland-Informationen werden zwischen Symbolen mit einem `SymTagCompiland`-Tag aufgeteilt, das abgerufen werden kann, ohne dass zusätzliche Kompilierungen und Symbole geladen werden, sowie von Symbolen mit einem `SymTagCompilandDetails`-Tag, das möglicherweise zusätzliche Symbole lädt.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.

|property|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`, wenn Bearbeiten und fortfahren bei der Kompilierung aktiviert wurde.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Das Symbol für die exe-Datei.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|Der Name der Bibliothek oder Objektdatei, aus der das Objekt geladen wurde.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Dateiname der Objektdatei der Kompilierungen.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|Der Name der Quelldatei.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompiland` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|

## <a name="see-also"></a>Siehe auch
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
- [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)