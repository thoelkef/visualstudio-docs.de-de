---
title: "IDiaTable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaTable-Schnittstelle"
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet Durchmesser\-Datenquellen eine Tabelle auf.  
  
## Syntax  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaTable`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaTable::get\_\_NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Ruft die [IEnumVARIANT Interface](http://msdn.microsoft.com/de-de/139e3c93-faef-4003-9079-e0e94494db3e)\-Version dieses Enumerators ab.|  
|[IDiaTable::get\_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Ruft den Namen der Tabelle ab oder legt ihn fest.|  
|[IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Ruft die Anzahl der Elemente in der Tabelle ab.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Ruft einen Verweis auf einen bestimmten Eintrags Index ab.|  
  
## Hinweise  
 Diese Schnittstelle implementiert die `IEnumUnknown`\-Enumerationsmethoden im Microsoft.VisualStudio.OLE.Interop\-Namespace.  Die `IEnumUnknown`\-Enumerationsschnittstelle kann zum Durchlaufen von Tabellen und [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md) die als Inhalt der [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)\-Methoden deutlich effizienter.  
  
 Die Interpretation der `IUnknown`\-Schnittstelle, die von der `IDiaTable::Item`\-Methode oder der `Next`\-Methode zurückgegeben wird \(im Microsoft.VisualStudio.OLE.Interop\-Namespace\) weist den Typ der Tabelle ab.  Wenn beispielsweise die `IDiaTable`\-Schnittstelle eine Liste mit eingefügten Quellen darstellt, sollte die `IUnknown`\-Schnittstelle für die [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)\-Schnittstelle abgefragt werden.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) oder [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)\-Methoden aufgerufen werden.  
  
 Die folgenden Schnittstellen werden mit der `IDiaTable`\-Schnittstelle implementiert \(das heißt Sie können die `IDiaTable`\-Schnittstelle für eine der folgenden Schnittstellen abfragen\):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## Beispiel  
 Die erste Funktion, `ShowTableNames`, werden die Namen aller Tabellen in der Sitzung an.  Die zweite Funktion, `GetTable`allen Tabellen durchsucht, für eine Tabelle, die eine angegebene Schnittstelle implementiert.  Die dritte Funktion, `UseTable`, wird gezeigt, wie die `GetTable`\-Funktion verwendet.  
  
> [!NOTE]
>  `CDiaBSTR` ist eine Klasse, die `BSTR` behandelt und automatisch durchgeführt wird, die die Zeichenfolge freigeben, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
```cpp#  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)