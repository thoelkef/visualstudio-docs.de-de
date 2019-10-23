---
title: Idiaenumsectioncontrisb | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e332bacdeaeca00d4e43d80807ee5f95c51c7e93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744250"
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
Listet die verschiedenen Abschnitts Beiträge auf, die in der Datenquelle enthalten sind.

## <a name="syntax"></a>Syntax

```
IDiaEnumSectionContribs : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaEnumSectionContribs` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Ruft die Version der [IEnumVARIANT-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dieses Enumerators ab.|
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|Ruft die Anzahl der Abschnitts Beiträge ab.|
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Ruft Abschnitts Beiträge mithilfe eines Indexes ab.|
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|Ruft eine angegebene Anzahl von Abschnitts Beiträgen in der enumerationssequenz ab.|
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|Überspringt eine angegebene Anzahl von Abschnitts Beiträgen in einer enumerationssequenz.|
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|

## <a name="remarks"></a>Hinweise

## <a name="note-for-callers"></a>Hinweis für Aufrufer
Rufen Sie diese Schnittstelle von der [IDiaSession:: getenumschlag Tables](../../debugger/debug-interface-access/idiasession-getenumtables.md) -Methode ab. Weitere Informationen finden Sie im Beispiel.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie Sie die-`GetEnumSectionContribs`-Funktion abrufen und die `IDiaEnumSectionContribs`-Schnittstelle (die `ShowSectionContribs`-Funktion) verwenden. Ein ausführeres Beispiel für die Verwendung von Abschnitts Beiträgen finden Sie unter [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Schnittstelle.

```C++

IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pUnknown    = NULL;
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);
    IDiaEnumTables*          pEnumTables = NULL;
    IDiaTable*               pTable      = NULL;
    ULONG                    celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}

void ShowSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pEnumSectionContribs;

    pEnumSectionContribs = GetEnumSectionContribs(pSession);
    if (pSectionContrib != NULL)
    {
        IDiaSectionContrib* pSectionContrib;
        ULONG celt = 0;

        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&
              celt == 1)
        {
            PrintSectionContrib(pSectionContrib, pSession);
            pSectionContrib->Release();
        }
        pSectionContrib->Release();
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
