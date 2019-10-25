---
title: 'Idiasymmetribol:: get_addressOffset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9290173fc9dcfdc07c7c0afbb33c741fe3e53f6c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741088"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Ruft den Offset Teil eines Adress Speicher Orts ab. Verwenden Sie, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf `LocIsStatic` festgelegt ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Offset Teil eines Adress Speicher Orts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Bei statischen Membern, die sich in einer externen DLL befinden, kann der Offset, der von dieser Methode zurückgegeben wird, 0 sein, da diese Methode das Abrufen der virtuellen Adresse des Members erfordert. Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::p ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle mit einem Parameter ungleich NULL aufgerufen wurde, der die Lade Adresse der DLL angibt.

 Um den Abschnitts Teil einer Adresse abzurufen, nennen Sie die [idiasymmetribol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) -Methode.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)