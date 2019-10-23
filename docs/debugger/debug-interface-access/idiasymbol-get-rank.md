---
title: 'Idiasymmetribol:: get_rank | Microsoft-Dokumentation'
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
ms.openlocfilehash: c5cff86464a4034ad869cdfe231a88ad128dbf52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739487"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Ruft den Rang (Anzahl der Dimensionen) eines mehrdimensionalen Fortran-Arrays ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Anzahl der Dimensionen in einem mehrdimensionalen Fortran-Array zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Rank bezieht sich auf die Anzahl der Dimensionen in einem Array, wobei das Array als `myarray[1,2,3]` deklariert wird. Dieses Beispiel weist einen Rang von 3 und 3 Dimensionen auf. Der Rang gilt C++ nicht für, wobei das Konzept eines Arrays von Arrays für jede Dimension verwendet (d. h. `myarray[1][2][3]`).

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)