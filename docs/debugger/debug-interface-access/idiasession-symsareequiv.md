---
title: 'IDiaSession:: symsAreEquiv | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741865"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Prüft, ob zwei Symbole äquivalent sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parameter
 `symbolA`

in Das erste [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das beim Vergleich verwendet wird.

 `symbolB`

in Das zweite `IDiaSymbol` im Vergleich verwendete Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Symbole gleichwertig sind, wird `S_OK` zurückgegeben. Andernfalls gibt `S_FALSE` zurück, die Symbole sind nicht äquivalent. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)