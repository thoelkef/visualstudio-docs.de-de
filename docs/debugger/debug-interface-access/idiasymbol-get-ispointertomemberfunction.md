---
title: 'Idiasymmetribol:: get_isPointerToMemberFunction | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1cbbc9a38ef8d92233175380455fbe8c8291263
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740107"
---
# <a name="idiasymbolget_ispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
Gibt an, ob dieses Symbol ein Zeiger auf eine Element Funktion ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isPointerToMemberFunction(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Ein Zeiger auf eine `BOOL`, die angibt, ob dieses Symbol ein Zeiger auf eine Element Funktion ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)