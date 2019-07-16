---
title: IDiaSymbol::get_liveRangeStartAddressSection | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99b5a14a321a28bdbe7337dcc7cdfa5febdad5d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786531"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Gibt zurück, den Teil "Abschnitt" die Startadresse des Bereichs, in dem die lokalen Symbolcache gültig ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Parameter
 `section`

[out] Gibt zurück, den Teil "Abschnitt" Bereich ab.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Ein Fehlercode bedeutet, dass das Symbol nicht live Bereichsinformationen verfügt.

## <a name="remarks"></a>Hinweise
 Die gebildet, indem Sie den Abschnitt und den Offset-Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.

 Verwenden Sie zum Abrufen der Zeitzonenoffset-Teils der Adresse [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)