---
title: 'Idiasymbol:: Get_hasseh | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41987007dd5121dff8cce1eb91ea9e1c4d93578c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401435"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
Ruft ein Flag, das angibt, ob die Funktion enthält [strukturierte Ausnahmebehandlung (C# /C++)](/cpp/cpp/structured-exception-handling-c-cpp) (z. B. __try /\__except-Blöcke).

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Gibt `TRUE` , wenn die Funktion strukturierte Ausnahmebehandlungsblöcke; hat, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Strukturierte Ausnahmebehandlung (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)