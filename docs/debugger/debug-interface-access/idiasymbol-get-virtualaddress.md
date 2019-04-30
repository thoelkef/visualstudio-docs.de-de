---
title: 'Idiasymbol:: Get_virtualaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualAddress method
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa09e0e40250d1e7d40ec0f85adca617852919f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401289"
---
# <a name="idiasymbolgetvirtualaddress"></a>IDiaSymbol::get_virtualAddress
Ruft die virtuelle Adresse (VA) des Speicherorts ab. Verwenden, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsStatic`.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die virtuelle Adresse des Speicherorts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)