---
title: 'Idiasectioncontrib:: Get_notpaged | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fb132b4cf36eb686424e0f756ffe0387a432eb0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610995"
---
# <a name="idiasectioncontribgetnotpaged"></a>IDiaSectionContrib::get_notPaged
Ruft ein Flag, das angibt, ob der Abschnitt nicht genügend Arbeitsspeicher ausgelagert werden kann.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_notPaged ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`
- [Out, Retval] Gibt `TRUE` gibt zurück, wenn Sie im Abschnitt ausgelagert werden kann, andernfalls, `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)