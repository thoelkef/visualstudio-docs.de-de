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
ms.openlocfilehash: 34a38766aeefdea3463a5ce1b94c374d618712fa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644640"
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
>  Ein Fehlercode bedeutet, dass das Symbol nicht live Bereichsinformationen verfügt.

## <a name="remarks"></a>Anmerkungen
 Die gebildet, indem Sie den Abschnitt und den Offset-Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.

 Verwenden Sie zum Abrufen der Zeitzonenoffset-Teils der Adresse [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)