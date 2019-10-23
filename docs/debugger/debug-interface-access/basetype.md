---
title: BaseType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BaseType symbol [DIA SDK]
ms.assetid: 2f9e22e6-8360-496a-ac6b-17a5a56b0c46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fbf1366c069139660c242bb27264c0a516fba22
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745515"
---
# <a name="basetype"></a>BaseType
Basis Typen werden `SymTagBaseType` Symbolen identifiziert.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind zusätzliche gültige Eigenschaften für diesen Symboltyp aufgeführt.

|property|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Einer der Werte der [BasicType-Enumeration](../../debugger/debug-interface-access/basictype.md).|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, wenn der Basistyp als konstant markiert ist.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Größe (in Bytes) des Basistyps.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol der einschließenden [Kompilierungen](../../debugger/debug-interface-access/compiland.md).|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagBaseType` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, wenn der Basistyp nicht ausgerichtet ist.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, wenn der Basistyp als flüchtig markiert ist.|

## <a name="see-also"></a>Siehe auch
- [BasicType-Enumeration](../../debugger/debug-interface-access/basictype.md)
- [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)