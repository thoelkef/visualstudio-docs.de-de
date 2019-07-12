---
title: 'Idiasymbol:: Get_isdataaligned | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8a46b84ff8af4163d6341f1cabbbe339379c0de
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808845"
---
# <a name="idiasymbolgetisdataaligned"></a>IDiaSymbol::get_isDataAligned
Ruft ein Flag, das angibt, ob es sich bei der benutzerdefinierten Typ (UDT) verfügt über einige bestimmte Speichergrenze ausgerichtet wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Gibt `TRUE` , wenn der UDT hat einige Speichergrenze; ausgerichtet wurde, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft wird in der Regel festgelegt, wenn die ausführbare Datei mit nicht standardmäßigen datenausrichtung kompiliert wird. Z. B. Microsoft C++-Compiler kann ändern, die datenausrichtung mit der Befehlszeilenoption/Zp<em>#</em>, wobei *#* ist ein Byte-Wert.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)