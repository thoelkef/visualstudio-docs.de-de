---
title: 'Idiasymmetribol:: get_addressSection | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a468fe6ee8a8d7d00bb2e6c261d50919a1dd764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741074"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Ruft den Abschnitts Teil eines Adress Speicher Orts ab. Verwenden Sie, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf `LocIsStatic` festgelegt ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Abschnitts Teil eines Adress Speicher Orts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Für statische Member, die sich in einer externen DLL befinden, kann der von dieser Methode zurückgegebene Abschnitt 0 sein, da diese Methode darauf basiert, dass die virtuelle Adresse des Members erhalten wird. Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::p ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle mit einem Parameter ungleich NULL aufgerufen wurde, der die Lade Adresse der DLL angibt.

 Um den Offset Teil einer Adresse abzurufen, nennen Sie die [idiasymmetribol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) -Methode.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)