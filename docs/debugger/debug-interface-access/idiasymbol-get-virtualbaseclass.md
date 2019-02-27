---
title: 'Idiasymbol:: Get_virtualbaseclass | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseClass method
ms.assetid: 474eddc6-bf16-4731-9145-6db2f2a0b4fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7773dfdecff4e56783765ccdedfa2feacf9c7b06
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616208"
---
# <a name="idiasymbolgetvirtualbaseclass"></a>IDiaSymbol::get_virtualBaseClass
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp eine virtuelle Basisklasse ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_virtualBaseClass ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` ist der benutzerdefinierte Datentyp eine virtuelle Basisklasse ist; andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)