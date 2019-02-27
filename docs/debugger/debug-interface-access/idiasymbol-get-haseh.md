---
title: 'Idiasymbol:: Get_haseh | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 475771d85a408238539a6faa0d8ce1eab6ec273c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617547"
---
# <a name="idiasymbolgethaseh"></a>IDiaSymbol::get_hasEH
Ruft ein Flag, das angibt, ob die Funktion nicht verwaltete Ausnahmebehandlung für C++-Stil (z. B. einen Try/Catch-Block) enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hasEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Gibt `TRUE` , wenn die Funktion die Ausnahmebehandlung im C++-Stil; hat, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)