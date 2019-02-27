---
title: 'Idiasymbol:: Get_volatiletype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6ccafc8a0d30558f61bc869d8cfc8280c04723e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616312"
---
# <a name="idiasymbolgetvolatiletype"></a>IDiaSymbol::get_volatileType
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp (UDT) "volatile" ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` gibt zurück, wenn der UDT flüchtig ist; andernfalls ist, `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 In C++ kann ein UDT mit gekennzeichnet werden die `volatile` Schlüsselwort Gibt an, dass sein Inhalt wird angenommen, dass darf nicht vor einem Zugriff auf die nächste vorhanden sein.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)