---
title: THUNK_ORDINAL | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613270"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Legt fest, Thunk-Typen.

## <a name="syntax"></a>Syntax

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Elements
Standard THUNK_ORDINAL_NOTYPE Thunk.

THUNK_ORDINAL_ADJUSTOR ein `this` Abwicklung Thunk.

Virtuelle THUNK_ORDINAL_VCALL Thunk für Aufruf.

Thunk für THUNK_ORDINAL_PCODE-P-Code.

THUNK_ORDINAL_LOAD verzögert geladenen Thunk.

Inkrementelle THUNK_ORDINAL_TRAMP_INCREMENTAL Trampoline Thunk (ein Thunk Trampoline wird verwendet, um die Aufrufe aus einem Speicher in einen anderen zu springen).

THUNK_ORDINAL_TRAMP_BRANCHISLAND Branch Punkt Trampoline Thunk.

## <a name="remarks"></a>Anmerkungen
Die Werte in dieser Enumeration werden zurückgegeben, von einem Aufruf der [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
