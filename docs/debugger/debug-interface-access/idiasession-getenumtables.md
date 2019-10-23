---
title: 'IDiaSession:: getenumschlag Tables | Microsoft-Dokumentation'
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
ms.openlocfilehash: 41679304986f5de948119a2958524b8f269ceb42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741925"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Ruft einen Enumerator für alle Tabellen ab, die im Symbol Speicher enthalten sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parameter
`ppEnumTables`

vorgenommen Gibt ein [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) -Objekt zurück. Verwenden Sie diese Schnittstelle, um die Tabellen im Symbol Speicher aufzulisten.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Dieses Beispiel stellt eine allgemeine Funktion dar, die die `getEnumTables`-Methode verwendet, um ein bestimmtes Enumeratorobjekt abzurufen. Wenn der Enumerator gefunden wird, gibt die Funktion einen Zeiger zurück, der in die gewünschte Schnittstelle umgewandelt werden kann. Andernfalls gibt die Funktion `NULL` zurück.

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
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
