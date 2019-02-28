---
title: 'Idiasymbol:: Get_hassecuritychecks | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4c54c6523caf08e367f245dd92fb7b91470ae0d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624853"
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Ruft ein Flag, das angibt, ob die Kompiliereinheit oder die Funktion Pufferüberlauf sicherheitsüberprüfungen kompiliert wurde (z. B. die [/GS (Puffer-Sicherheitsüberprüfung)](/cpp/build/reference/gs-buffer-security-check) Compilerschalter).

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Gibt `TRUE` , wenn die Funktion sicherheitsüberprüfungen; hat, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (Puffersicherheitsüberprüfung)](/cpp/build/reference/gs-buffer-security-check)