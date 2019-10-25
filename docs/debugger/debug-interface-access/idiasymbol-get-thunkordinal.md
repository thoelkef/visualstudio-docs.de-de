---
title: 'Idiasymmetribol:: get_thunkOrdinal | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3bc8c523886d694ea413dedcf9a28e53e361882b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739139"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Ruft den Thunk-Typ einer Funktion ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt einen Wert aus der [THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) -enumerationsenumeration zurück, der den THUNK-Typ einer Funktion angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft ist nur gültig, wenn das Symbol als [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswert `SymTagThunk`.

 Ein "Thunk" ist ein Code Ausschnitt, der zwischen einem 32-Bit-Speicher Adressraum (auch als flataddress-Raum bezeichnet) und einem 16-Bit-Adressraum (als segmentierter Adressraum bezeichnet) konvertiert.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Thunk_Ordinal-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)