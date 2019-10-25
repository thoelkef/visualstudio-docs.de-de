---
title: 'Idiasymmetribol:: get_liveRangeStartAddressSection | Microsoft-Dokumentation'
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
ms.openlocfilehash: a23f0661d8af6417d754fd7a71c66c5dd3ef1135
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739905"
---
# <a name="idiasymbolget_liverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Gibt den Abschnitts Teil der Startadresse des Bereichs zurück, in dem das lokale Symbol gültig ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Parameter
 `section`

vorgenommen Gibt den Abschnitts Teil des Start Adress Bereichs zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

> [!NOTE]
> Ein zurückgegebener Fehlercode bedeutet, dass das Symbol keine Informationen zum Live Bereich enthält.

## <a name="remarks"></a>Hinweise
 Die durch den Abschnitt und den Offset gebildete Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.

 Um den Offset Teil der Adresse zu erhalten, verwenden Sie [idiasymmetribol:: get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)