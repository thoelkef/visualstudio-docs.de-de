---
title: IDiaTable | Microsoft-Dokumentation
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
ms.openlocfilehash: 50d38204155e12f65856f60e2b9df7f10837b515
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920930"
---
# <a name="idiatable"></a>IDiaTable
Listet eine Tabelle in DIA-Datenquelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaTable`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Ruft die [IEnumVARIANT-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) Version von diesem Enumerator.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Ruft den Namen der Tabelle ab.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Ruft die Anzahl der Elemente in der Tabelle ab.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Ruft einen Verweis auf einen bestimmten Eintrag Index ab.|  
  
## <a name="remarks"></a>Anmerkungen  
 Diese Schnittstelle implementiert, die `IEnumUnknown` Enumerationsmethoden im Microsoft.VisualStudio.OLE.Interop-Namespace. Die `IEnumUnknown` Enumerationsschnittstelle ist wesentlich effizienter, für den Inhalt der Tabelle als Durchlaufen der [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md) und [idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md) Methoden.  
  
 Die Interpretation der der `IUnknown` Schnittstelle zurückgegeben wird, entweder die `IDiaTable::Item` Methode oder der `Next` -Methode (in dem Namespace Microsoft.VisualStudio.OLE.Interop) richtet sich nach den Typ der Tabelle. Z. B. wenn die `IDiaTable` Schnittstelle stellt eine Liste von eingefügtem Quellen, die `IUnknown` Schnittstelle abgefragt werden muss, für die [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) oder [idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) Methoden.  
  
 Die folgenden Schnittstellen implementiert werden, mit der `IDiaTable` Schnittstelle (d. h. Sie können Abfragen, die `IDiaTable` Schnittstelle für eine der folgenden Schnittstellen):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Beispiel  
 Die erste Funktion, `ShowTableNames`, zeigt die Namen aller Tabellen in der Sitzung. Die zweite Funktion `GetTable`, sucht alle Tabellen für eine Tabelle, die eine angegebene Schnittstelle implementiert. Die dritte Funktion `UseTable`, zeigt, wie die `GetTable` Funktion.  
  
> [!NOTE]
>  `CDiaBSTR` ist eine Klasse, umschließt ein `BSTR` und übernimmt automatisch das Freigeben der Zeichenfolge, bei die Instanziierung den Gültigkeitsbereich verlässt.  
  
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
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)