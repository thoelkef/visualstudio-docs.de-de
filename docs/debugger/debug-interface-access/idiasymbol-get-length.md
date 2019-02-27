---
title: 'Idiasymbol:: Get_length | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57aeb77b965cbb45ab282be728e164a2f472f49b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626283"
---
# <a name="idiasymbolgetlength"></a>IDiaSymbol::get_length
Ruft die Anzahl der Bits oder Bytes an Arbeitsspeicher ein, die das Objekt, das durch dieses Symbol dargestellt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Anzahl von Bytes oder Bits im Arbeitsspeicher ein, die das Objekt, das durch dieses Symbol dargestellt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) des Symbols ist `LocIsBitField`, die von dieser Methode zurückgegebene Länge in Bits ist; andernfalls ist die Länge in Bytes für alle anderen Typen.

## <a name="example"></a>Beispiel

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)