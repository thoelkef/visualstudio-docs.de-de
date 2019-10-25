---
title: 'Idiasymmetribol:: get_baseType | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a3d1bb8b2f3095fd35488c47f823e7b3603995b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740921"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
Ruft den Basistyp für dieses Symbol ab<em>.</em>

## <a name="syntax"></a>Syntax

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
`pRetVal`

vorgenommen Gibt einen Wert aus der [BasicType](../../debugger/debug-interface-access/basictype.md) -enumerationsenumeration zurück, der den Basistyp des Symbols angibt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
Der Basistyp für ein Symbol kann bestimmt werden, indem zuerst der Typ des Symbols und dann der zurückgegebene Typ für den Basistyp abgefragt wird. Beachten Sie, dass einige Symbole keinen Basistyp haben können – z. b. einen Struktur Namen.

## <a name="example"></a>Beispiel

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType-Enumeration](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
