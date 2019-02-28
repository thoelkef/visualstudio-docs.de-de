---
title: PointerType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PointerType symbol
ms.assetid: 67228681-7345-4537-8af3-93806803ee96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4efed94939675a97322dc18e247a8e2546689b1c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607615"
---
# <a name="pointertype"></a>PointerType
Durch jeden Zeiger identifiziert eine `SymTagPointerType` Symbol.

## <a name="properties"></a>Eigenschaften
 Die folgende Tabelle zeigt zusätzliche gültige Eigenschaften für diesen Symboltyp.

|Eigenschaft|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Wenn der Zeiger als Konstante markiert ist.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Größe in Bytes, des Zeigers.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol des einschließenden [Kompiliereinheit](../../debugger/debug-interface-access/compiland.md).|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE` Wenn der Zeiger auf ein Verweistyp ist.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagPointerType` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Zielsymbol des Zeigers.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Die ID des Symbols Typ.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Wenn der Zeiger nicht ausgerichtete ist.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Wenn der Zeiger als flüchtig gekennzeichnet ist.|

## <a name="see-also"></a>Siehe auch
- [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)