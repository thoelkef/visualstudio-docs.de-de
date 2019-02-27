---
title: 'Idiasymbol:: Get_editandcontinueenabled | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ba760660a6dfaf97040a296a3ce7991b7ab4555
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606432"
---
# <a name="idiasymbolgeteditandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
Ruft ein Flag, der angibt, ob das Modul kompiliert wurde, mit der [/Z7, / Zi, / Zi (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format) Compilerschalter.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_editAndContinueEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` Wenn Bearbeiten und Fortfahren bei der Kompilierung; aktiviert wurde, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/Z7, /Zi, /ZI (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format)