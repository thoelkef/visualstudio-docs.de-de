---
title: 'Idiasectioncontrib:: Get_remove | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01b3eef646f9105d651a17b58100aad8b4869c3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616117"
---
# <a name="idiasectioncontribgetremove"></a>IDiaSectionContrib::get_remove
Ruft ein Flag, das angibt, ob der Abschnitt entfernt wird, bevor es Teil des in-Memory-Abbilds durchgeführt wird.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_remove ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn der Bereich ist nicht auf das Bild im Arbeitsspeicher hinzugefügt werden, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)