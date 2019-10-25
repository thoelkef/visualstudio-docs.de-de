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
ms.openlocfilehash: b39bf1e73d8b056c1cfcbfafd41dcbbb464c40ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739922"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Gibt den Offset Teil der Startadresse des Bereichs zurück, in dem das lokale Symbol gültig ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parameter
 `offset`

vorgenommen Gibt den Offset Teil des Start Adress Bereichs zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

> [!NOTE]
> Ein zurückgegebener Fehlercode bedeutet, dass das Symbol keine Informationen zum Live Bereich enthält.

## <a name="remarks"></a>Hinweise
 Die durch den Abschnitt und den Offset gebildete Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.

 Um den Abschnitts Teil der Adresse zu erhalten, verwenden Sie [idiasymmetribol:: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)