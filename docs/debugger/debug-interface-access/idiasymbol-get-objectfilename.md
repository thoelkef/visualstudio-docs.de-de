---
title: IDiaSymbol::get_objectFileName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 841fe2b1ae6f54b3bc7deea97b335790ca6dac5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611814"
---
# <a name="idiasymbolgetobjectfilename"></a>IDiaSymbol::get_objectFileName
Ruft ab, der Name der Objektdatei.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_objectFilename(
   BSTR *pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `BSTR` , enthält der Name der Objektdatei.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)