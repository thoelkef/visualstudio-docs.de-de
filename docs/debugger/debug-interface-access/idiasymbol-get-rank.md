---
title: 'Idiasymbol:: Get_rank | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 646672904aebb8e4c0fcdd5200b60c2a2349a859
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639283"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Ruft den Rang (Anzahl der Dimensionen) eines mehrdimensionalen Arrays von FORTRAN ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Anzahl der Dimensionen in ein mehrdimensionales Array von FORTRAN zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Rang bezieht sich auf die Anzahl der Dimensionen in einem Array, in dem das Array, als deklariert ist `myarray[1,2,3]`. In diesem Beispiel hat den Rang 3 und 3 Dimensionen. Rang gelten nicht für C++ das Konzept eines Arrays von Arrays für die einzelnen Dimensionen verwendet (d. h. `myarray[1][2][3]`).

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)