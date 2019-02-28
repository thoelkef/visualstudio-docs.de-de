---
title: 'Idiasymbol:: Get_nested | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_nested method
ms.assetid: 6ae46d43-8486-48d6-a6f2-d73ebf4023e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b4e44cb63129e79e993d57f3dbd49b2b63f8913
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644626"
---
# <a name="idiasymbolgetnested"></a>IDiaSymbol::get_nested
Ruft ein Flag, das angibt, ob der benutzerdefinierte Typ geschachtelt ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_nested ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn der benutzerdefinierte Datentyp geschachtelt ist; andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)