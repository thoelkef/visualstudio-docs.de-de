---
title: 'Idiasymmetribol:: get_isSplitted | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9511551a2f3530adc14bee0f6eec3cf360b41c03
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740049"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Ruft ein Flag ab, das angibt, ob das Daten Symbol in eine Aggregation oder Auflistung anderer Symbole aufgeteilt wurde. der Compiler behandelt die Symbole als separate Entitäten, auch wenn Sie tatsächlich Teil eines größeren Symbols sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn das Symbol in ein Aggregat von Symbolen aufgeteilt wurde. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE`-oder-Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Die [idiasymmetribol:: get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) -Methode gibt `TRUE` für alle Symbole zurück, die Teil eines Trenn Zeichens sind.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)