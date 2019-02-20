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
ms.openlocfilehash: 482c5f7bd0565c3b6ece124c88bd5e225b4cc7dd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318523"
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
THUNK_ORDINAL_NOTYPE  
Standard-Thunk.

THUNK_ORDINAL_ADJUSTOR  
Ein `this` Abwicklung Thunk.

THUNK_ORDINAL_VCALL  
Virtueller Aufruf Thunk.

THUNK_ORDINAL_PCODE  
Thunk für P-Code.

THUNK_ORDINAL_LOAD  
Verzögert Thunk.

THUNK_ORDINAL_TRAMP_INCREMENTAL  
Inkrementelle Trampoline-Thunk (ein Thunk Trampoline wird verwendet, um die Aufrufe aus einem Speicher in einen anderen zu springen).

THUNK_ORDINAL_TRAMP_BRANCHISLAND  
Branch Punkt Trampoline Thunk.

## <a name="remarks"></a>Anmerkungen
Die Werte in dieser Enumeration werden zurückgegeben, von einem Aufruf der [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
[Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
