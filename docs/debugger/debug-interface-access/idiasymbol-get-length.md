---
title: 'Idiasymmetribol:: get_Length | Microsoft-Dokumentation'
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
ms.openlocfilehash: 114d9f7b00bbe5d322e7b6893e96fbbabec9d002
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739981"
---
# <a name="idiasymbolget_length"></a>IDiaSymbol::get_length
Ruft die Anzahl der Bits oder Bytes des Arbeitsspeichers ab, die von dem durch dieses Symbol dargestellten Objekt verwendet werden.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Anzahl von Bytes oder Bits des Speichers zurück, die von dem durch dieses Symbol dargestellten Objekt verwendet werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) des Symbols `LocIsBitField` ist, ist die von dieser Methode zurückgegebene Länge in Bits. Andernfalls ist die Länge für alle anderen Speicherort Typen in Byte.

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
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)