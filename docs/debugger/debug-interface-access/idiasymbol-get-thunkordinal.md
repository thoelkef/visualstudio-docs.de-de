---
title: 'Idiasymbol:: Get_thunkordinal | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78ce8311e9504261399f22feefebb93fb9b3c64f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605951"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Ruft den Thunk-Typ, der eine Funktion ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt einen Wert aus der [THUNK_ORDINAL-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md) -Enumeration, die den Thunk-Typ, der eine Funktion angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Diese Eigenschaft gilt nur, wenn das Symbol als ein [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Wert `SymTagThunk`.

 Ein "Thunk" ist ein Codeabschnitt, der einen 16-Bit-Adressraum (als einen segmentierten Adressraum bezeichnet) bis ein Arbeitsspeicher von 32-Bit-Adressraum (auch bekannt als flache Adressraum) konvertiert.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Thunk_Ordinal-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)