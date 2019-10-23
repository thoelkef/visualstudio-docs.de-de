---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70265976e5c6e7c2b3f536f2b8648aaba44df528
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743859"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Ruft die vorherigen Symbole in der Order by-Adresse ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Symbole im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekten gefüllt werden soll, die die gewünschten Symbole darstellen.

 pceltFetched

vorgenommen Gibt die Anzahl der Symbole im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine vorherigen Symbole vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode aktualisiert die enumeratorposition um die Anzahl der abgerufenen Elemente.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)