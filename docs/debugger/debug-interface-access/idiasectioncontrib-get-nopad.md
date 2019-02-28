---
title: 'Idiasectioncontrib:: Get_nopad | Microsoft-Dokumentation'
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
ms.openlocfilehash: 51fb2c4ff2f27cee8fcc989139f5ae14c2641394
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642143"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Ruft ein Flag, der angibt, ob der Abschnitt nicht soll, können Sie auf die nächsten Begrenzung des Arbeitsspeichers aufgefüllt werden ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn der Abschnitt nicht soll, können Sie bis zur nächsten Arbeitsspeicher Begrenzung aufgefüllt werden; andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Dies ist eine Eigenschaft, die in der Regel nur für ältere Dateien angezeigt.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)