---
title: 'Idiasymmetribol:: get_isAggregated | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee36d1901f7acb5bc7e41ac72b8dc03b15bc45c8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740295"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Ruft ein Flag ab, das angibt, ob das Daten Symbol Teil eines Aggregats oder einer Auflistung von Symbolen ist. der Compiler behandelt aggregierte Symbole als separate Entitäten, Sie sind jedoch wirklich Teil eines einzigen größeren Symbols.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn die Daten Teil einer Aggregation von Symbolen sind, die von einem übergeordneten Symbol getrennt sind. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Die [idiasymmetribol:: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) -Methode wird für das Symbol `TRUE`, das das übergeordnete Element der aggregierten Symbole ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)