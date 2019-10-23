---
title: 'IDiaEnumSymbolsByAddr:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424924f3fab62cf862420d58c947bba16343141d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743881"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Ruft die nächsten Symbole in der Order by-Adresse ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Symbole im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit dem [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt ausgefüllt werden soll, das die gewünschten Symbole darstellt.

 pceltFetched

vorgenommen Gibt die Anzahl der Symbole im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Symbole vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode aktualisiert die enumeratorposition um die Anzahl der abgerufenen Elemente.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)