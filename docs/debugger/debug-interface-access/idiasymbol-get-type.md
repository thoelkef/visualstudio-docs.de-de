---
title: 'Idiasymbol:: Get_type | Microsoft-Dokumentation'
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
ms.openlocfilehash: a5550ed7551e58140301f6a434d252a534b78228
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227195"
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
Ruft ab, das Symbol, das den Typ für dieses Symbol darstellt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parameter
`pRetVal`  
[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das den Typ dieses Symbols darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
Um den Typ zu bestimmen, ein Symbol wurde, müssen Sie diese Methode aufrufen, und überprüfen Sie das Ergebnis [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt. Beachten Sie, dass es möglich, dass ein Symbol aus, die keinen Typ aufweisen. Beispielsweise der Namen einer Struktur hat keinen Typ, aber sie Symbole für untergeordnete Elemente verfügen kann (verwenden Sie die [idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) Methode, um die untergeordneten untersuchen).

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
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
