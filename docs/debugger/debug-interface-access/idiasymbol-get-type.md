---
title: 'Idiasymmetribol:: get_type | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f9b9fd91535cc16b96da530db8ab43c4eaabf2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739095"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Ruft das Symbol ab, das den Typ für dieses Symbol darstellt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parameter
`pRetVal`

vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das den Typ dieses Symbols darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
Um den Typ eines Symbols zu ermitteln, müssen Sie diese Methode aufzurufen und das resultierende [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt untersuchen. Beachten Sie, dass es möglich ist, dass ein Symbol keinen Typ hat. Der Name einer Struktur hat z. b. keinen Typ, kann aber untergeordnete Symbole aufweisen (verwenden Sie die [idiasymmetribol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) -Methode, um diese untergeordneten Elemente zu untersuchen).

## <a name="example"></a>Beispiel

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
