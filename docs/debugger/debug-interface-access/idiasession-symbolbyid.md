---
title: 'IDiaSession:: symbolById | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ffcb6c438150bff82f17a66c3347c300b17d72
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741880"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Ruft ein Symbol anhand seines eindeutigen Bezeichners ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parameter
`id`

in Eindeutiger Bezeichner.

`ppSymbol`

vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das abgerufene Symbol darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Der angegebene Bezeichner ist ein eindeutiger Wert, der vom Dia SDK intern verwendet wird, um alle Symbole eindeutig zu machen.

Diese Methode kann z. b. verwendet werden, um das Symbol abzurufen, das den Typ eines anderen Symbols darstellt (siehe Beispiel).

## <a name="example"></a>Beispiel
In diesem Beispiel wird ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt abgerufen, das den Typ eines anderen Symbols darstellt. In diesem Beispiel wird gezeigt, wie die `symbolById`-Methode in der Sitzung verwendet wird. Ein einfacherer Ansatz besteht darin, die [idiasymmetribol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) -Methode aufzurufen, um das Typsymbol direkt abzurufen.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
