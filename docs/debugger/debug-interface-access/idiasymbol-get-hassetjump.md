---
title: 'Idiasymmetribol:: get_hasSetJump | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac344c97c7e79ea0cd92cce743848f0ac6e7f99f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740449"
---
# <a name="idiasymbolget_hassetjump"></a>IDiaSymbol::get_hasSetJump
Ruft ein Flag ab, das angibt, ob die Funktion die Verwendung des [setjmp](/cpp/c-runtime-library/reference/setjmp) -Befehls enthält (gekoppelt mit dem [longjmp](/cpp/c-runtime-library/reference/longjmp) -Befehl, die die Methode der Ausnahmebehandlung im C-Stil bilden).

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hasSetJump(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn die Funktion einen `setjmp`-Befehl enthält. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE`-oder-Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)