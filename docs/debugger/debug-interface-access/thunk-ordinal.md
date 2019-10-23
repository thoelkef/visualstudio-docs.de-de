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
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738496"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Legt Thunk-Typen fest.

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
THUNK_ORDINAL_NOTYPE-Standard Thunk.

THUNK_ORDINAL_ADJUSTOR eine `this`-oder-Thunk.

THUNK_ORDINAL_VCALL virtueller callthunk.

THUNK_ORDINAL_PCODE P-Code Thunk.

THUNK_ORDINAL_LOAD verzögertes Laden Thunk.

THUNK_ORDINAL_TRAMP_INCREMENTAL inkrementelles Trampolin-THUNK (ein Trampolin-THUNK wird verwendet, um Aufrufe von einem Speicherplatz zu einem anderen zu überspringen).

THUNK_ORDINAL_TRAMP_BRANCHISLAND-Kernstück-Trampolin-Thunk.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
