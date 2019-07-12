---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0312571b0a96b080949398618888b05c2704d3ca
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808945"
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Gibt den Zeitzonenoffset-Teil der Startadresse des Bereichs, in dem die lokalen Symbolcache gültig ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parameter
 `offset`

[out] Gibt den Zeitzonenoffset-Teil des Adressbereichs ab.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Ein Fehlercode bedeutet, dass das Symbol nicht live Bereichsinformationen verfügt.

## <a name="remarks"></a>Hinweise
 Die gebildet, indem Sie den Abschnitt und den Offset-Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.

 Verwenden Sie zum Abrufen des Teils "Abschnitt" die Adresse [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)