---
title: 'Idiasymmetribol:: get_Offset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: feb7620e507c5e57cf025211e42d541440af22f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739573"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
Ruft den Offset der Symbol Position ab. Verwenden Sie, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` oder `LocIsBitField` ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Offset der Symbol Position in Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Der Offset ist von einem bekannten, zuvor festgelegten Zeitpunkt. Beispielsweise ist der Offset für einen `LocIsBitField` Location-Typ in der Regel vom Anfang der enthaltenden Klasse.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)