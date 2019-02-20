---
title: 'Idiasession:: Symbolbyid | Microsoft-Dokumentation'
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
ms.openlocfilehash: 71072c597a445d54fc3429e949b24fde81761fc1
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227669"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Ruft ein Symbol durch seinen eindeutigen Bezeichner ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parameter
`id`  
[in] Eindeutiger Bezeichner.

`ppSymbol`  
[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das Symbol darstellt, abgerufen.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
Der angegebene Bezeichner ist ein eindeutiger Wert wird intern vom DIA-SDK verwendet, um alle Symbole eindeutig zu machen.

Diese Methode kann verwendet werden, z. B. das Symbol, der den Typ der ein anderes Symbol abrufen (siehe Beispiel).

## <a name="example"></a>Beispiel
Ruft ab, in diesem Beispiel wird ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , die den Typ der ein anderes Symbol darstellt. Dieses Beispiel zeigt, wie Sie mit der `symbolById` -Methode in der Sitzung. Ein einfacher Ansatz ist, rufen Sie die [idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) Methode, um das Typsymbol direkt abrufen.

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
[IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
