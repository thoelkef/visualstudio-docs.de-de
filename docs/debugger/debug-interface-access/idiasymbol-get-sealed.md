---
title: 'Idiasymbol:: Get_sealed | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c75148fdf8453590be7eb0f9fbde95e4bb4b981
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64791683"
---
# <a name="idiasymbolgetsealed"></a>IDiaSymbol::get_sealed
Ruft ein Flag, das angibt, ob die Klasse oder Methode versiegelt ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_sealed( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn die Klasse oder Methode versiegelt ist; andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Hinweise
 Eine versiegelte Klasse kann nicht als Basisklasse verwendet werden. Eine versiegelte Methode darf nicht außer Kraft gesetzt sein.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)