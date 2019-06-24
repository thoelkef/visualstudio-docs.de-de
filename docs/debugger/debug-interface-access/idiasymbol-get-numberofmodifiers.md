---
title: IDiaSymbol::get_numberOfModifiers | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74a83a83a805aa86d10b3c051ac1c6fc39f36f14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62835984"
---
# <a name="idiasymbolgetnumberofmodifiers"></a>IDiaSymbol::get_numberOfModifiers
Ruft die Anzahl der Modifizierer, die in den ursprünglichen Typ angewendet werden.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_numberOfModifiers(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `DWORD` , der angibt, dass der Anzahl der Modifizierer, die in den ursprünglichen Typ angewendet werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)