---
title: 'Idiasymmetribol:: get_registerId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739463"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Ruft den Register Kenn Zeichner des Speicher Orts ab, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf `LocIsEnregistered` festgelegt ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Register Kenn Zeichner des Speicher Orts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Wenn das Symbol relativ zu einem Register ist, d. h., wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) des Symbols auf `LocIsRegRel` festgelegt ist, verwenden Sie die `get_registerId`-Methode gefolgt von einem Aufruf der [idiasymmetribol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) -Methode, um den Offset aus dem Register abzurufen, bei dem das Symbol ist. befindet.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)