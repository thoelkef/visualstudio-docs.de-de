---
title: 'Idiasymmetribol:: get_isSingleInheritance | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96a8ce072fc57dc236dd2025b8ea3c9c5a4b9b79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740060"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Gibt an, ob der `this` Zeiger auf einen Datenmember mit einzelner Vererbung zeigt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Ein Zeiger auf einen `BOOL`, der angibt, ob der `this` Zeiger auf einen Datenmember mit einzelner Vererbung zeigt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)