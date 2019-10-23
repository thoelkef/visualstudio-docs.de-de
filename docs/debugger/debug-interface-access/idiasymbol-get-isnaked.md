---
title: 'Idiasymmetribol:: get_isNaked | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 684fd10b7899e0ed82b4b93a6182eea2a2447e0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740160"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
Ruft ein Flag ab, das angibt, ob die Funktion über das [Naked](/cpp/cpp/naked-cpp) -Attribut verfügt (d. h., die Funktion verfügt über keinen Prolog-oder Epilogcode, der vom Compiler hinzugefügt wurde).

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn die Funktion über das `naked`-Attribut verfügt. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Naked-Funktionsaufrufe](/cpp/cpp/naked-function-calls)