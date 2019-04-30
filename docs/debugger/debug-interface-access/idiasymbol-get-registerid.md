---
title: 'Idiasymbol:: Get_registerid | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3e2b1cbb6837ca139e735bef17bc0c2712d9cae7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400204"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Ruft ab, der Register-Kennzeichner des Standorts bei der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsEnregistered`.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Register-Kennzeichner des Speicherorts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="remarks"></a>Hinweise
 Wenn das Symbol Bezug auf ein Register, d. h. wenn des Symbols [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsRegRel`, verwenden Sie die `get_registerId` Methode, gefolgt von einem Aufruf von der [idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Methode, die der Offset aus der Registrierung abgerufen werden, wo sich das Symbol befindet.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)