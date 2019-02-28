---
title: 'Idiasymbol:: Get_arrayindextype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexType method
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44aedd4bf1d5b4127839c6a061948b2c393a0f7b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597295"
---
# <a name="idiasymbolgetarrayindextype"></a>IDiaSymbol::get_arrayIndexType
Ruft die Symbol-Schnittstelle des Arraytyps Index des Symbols ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_arrayIndexType ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das den Typ des Array-Index des Symbols darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Einige Sprachen können es sich um den Typ als Index in ein Array angeben. Das von dieser Methode zurückgegebene Symbol gibt an, diesen Typ.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)