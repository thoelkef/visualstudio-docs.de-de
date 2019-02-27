---
title: 'Idiasymbol:: Get_noreturn | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cd768220b25ec93ffdb4f038db475304db71333
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605535"
---
# <a name="idiasymbolgetnoreturn"></a>IDiaSymbol::get_noReturn
Ruft ein Flag, das angibt, ob die Funktion markiert ist, als die kein Ergebnis zurückgegeben, mit der [Noreturn](/cpp/cpp/noreturn) Attribut.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_noReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 pFlag

[out] Gibt `TRUE` , wenn die Funktion deklariert wurde, als nicht zurückgeben, mit der `noreturn` Attribut zurückgegeben; andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [noreturn](/cpp/cpp/noreturn)