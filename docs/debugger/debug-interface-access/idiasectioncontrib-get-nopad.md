---
title: 'IDiaSectionContrib:: get_nopad | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a81113242379070e56d6d0bd0f916355985eaa42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742625"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
Ruft ein Flag ab, das angibt, ob der Abschnitt nicht an der nächsten Speichergrenze aufgefüllt werden soll.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn der Abschnitt nicht an der nächsten Speichergrenze aufgefüllt werden soll. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Dies ist eine Eigenschaft, die in der Regel nur für ältere Dateien sichtbar ist.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)