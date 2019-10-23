---
title: Idisierbar | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738709"
---
# <a name="idiatable"></a>IDiaTable
Listet eine Dia-Datenquellen Tabelle auf.

## <a name="syntax"></a>Syntax

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaTable` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Ruft die Version der [IEnumVARIANT-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dieses Enumerators ab.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Ruft den Namen der Tabelle ab.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Ruft die Anzahl der Elemente in der Tabelle ab.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Ruft einen Verweis auf einen bestimmten Eintrags Index ab.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle implementiert die `IEnumUnknown` Enumerationsmethoden im Microsoft. VisualStudio. OLE. Interop-Namespace. Die `IEnumUnknown` Enumerationsschnittstelle ist viel effizienter zum Durchlaufen der Tabelleninhalte als die [idisierbare:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) -Methode und die [iditable:: Item](../../debugger/debug-interface-access/idiatable-item.md) -Methode.

Die Interpretation der `IUnknown`-Schnittstelle, die entweder von der `IDiaTable::Item`-Methode oder der `Next`-Methode (im Microsoft. VisualStudio. OLE. Interop-Namespace) zurückgegeben wurde, hängt vom Typ der Tabelle ab. Wenn die `IDiaTable`-Schnittstelle z. b. eine Liste von injizierten Quellen darstellt, sollte die `IUnknown`-Schnittstelle für die [idiainjetedsource](../../debugger/debug-interface-access/idiainjectedsource.md) -Schnittstelle abgefragt werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) -Methode oder der [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) -Methode ab.

Die folgenden Schnittstellen werden mit der `IDiaTable`-Schnittstelle implementiert (d. h., Sie können die `IDiaTable`-Schnittstelle für eine der folgenden Schnittstellen Abfragen):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Beispiel
Mit der ersten Funktion (`ShowTableNames`) werden die Namen aller Tabellen in der Sitzung angezeigt. Die zweite Funktion, `GetTable`, durchsucht alle Tabellen nach einer Tabelle, die eine angegebene Schnittstelle implementiert. Die dritte Funktion, `UseTable`, zeigt, wie Sie die `GetTable`-Funktion verwenden.

> [!NOTE]
> `CDiaBSTR` ist eine Klasse, die eine `BSTR` umschließt und die Freigabe der Zeichenfolge automatisch verarbeitet, wenn die Instanziierung den Gültigkeitsbereich verlässt.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
