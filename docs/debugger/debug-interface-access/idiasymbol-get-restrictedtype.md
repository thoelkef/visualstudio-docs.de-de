---
title: IDiaSymbol::get_restrictedType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8929414c0e36983d378ea2a801803321f3aa88c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598192"
---
# <a name="idiasymbolgetrestrictedtype"></a>IDiaSymbol::get_restrictedType
Gibt an, ob die `this` Zeiger markiert wird als beschränkt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_restrictedType(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `BOOL` , der angibt, ob die `this` Zeiger markiert wird als beschränkt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)