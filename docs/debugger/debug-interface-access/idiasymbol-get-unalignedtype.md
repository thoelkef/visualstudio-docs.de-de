---
title: 'Idiasymbol:: Get_unalignedtype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unalignedType method
ms.assetid: fdcb38fb-490e-4d15-b4e5-3770043a366c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af79f4074d3eb7e370d3e4fb24984e70ed2d962a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606224"
---
# <a name="idiasymbolgetunalignedtype"></a>IDiaSymbol::get_unalignedType
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp nicht ausgerichtete ist ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_unalignedType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` gibt zurück, wenn der benutzerdefinierte Datentyp, andernfalls nicht ausgerichtete ist, `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)