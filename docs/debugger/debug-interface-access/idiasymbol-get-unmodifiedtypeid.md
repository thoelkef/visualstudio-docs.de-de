---
title: IDiaSymbol::get_unmodifiedTypeId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99d549a0edc56d48d686424c35f22fc7ea74438b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613166"
---
# <a name="idiasymbolgetunmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
Ruft die ID des ursprünglichen Typs (unverändert) ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_unmodifiedTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `DWORD` , enthält die-ID.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)