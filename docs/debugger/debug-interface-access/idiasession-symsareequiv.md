---
title: 'Idiasession:: Symsareequiv | Microsoft-Dokumentation'
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
ms.openlocfilehash: 0253104cf29e86825fadc8c8bd18133e0d3cf593
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839074"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Überprüft, um festzustellen, ob zwei Symbole entsprechen.

## <a name="syntax"></a>Syntax

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parameter
 `symbolA`

[in] Die erste [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das im Vergleich verwendet.

 `symbolB`

[in] Die zweite `IDiaSymbol` Objekt, das im Vergleich verwendet.

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, wenn die Symbole gleichwertig sind, `S_OK`ist, andernfalls gibt `S_FALSE`, die Symbole sind kein Äquivalent. Geben Sie andernfalls einen Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)