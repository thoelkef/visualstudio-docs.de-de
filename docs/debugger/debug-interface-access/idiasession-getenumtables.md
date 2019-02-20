---
title: 'Idiasession:: Getenumtables | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c331171a62d2319666229f108428b9d62b7464e
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227617"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Ruft einen Enumerator für alle Tabellen im Symbolspeicher ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parameter
`ppEnumTables`  
[out] Gibt eine [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) Objekt. Verwenden Sie diese Schnittstelle zum Aufzählen der Tabellen im Symbolspeicher.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt eine allgemeine Funktion, verwendet der `getEnumTables` Methode, um eine bestimmte Enumerator-Objekt abzurufen. Wenn der Enumerator gefunden wird, gibt die Funktion einen Zeiger, der umgewandelt werden kann, die gewünschte Schnittstelle zurück; die Funktion hingegen gibt `NULL`.

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Siehe auch
[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
[IDiaSession](../../debugger/debug-interface-access/idiasession.md)
