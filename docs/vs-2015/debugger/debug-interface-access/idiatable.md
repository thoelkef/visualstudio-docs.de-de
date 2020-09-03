---
title: Idisierbar | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682788"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Listet eine Dia-Datenquellen Tabelle auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaTable` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Ruft die Version der [IEnumVARIANT-Schnittstelle](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) dieses Enumerators ab.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Ruft den Namen der Tabelle ab.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Ruft die Anzahl der Elemente in der Tabelle ab.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Ruft einen Verweis auf einen bestimmten Eintrags Index ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle implementiert die `IEnumUnknown` Enumerationsmethoden im Microsoft. VisualStudio. OLE. Interop-Namespace. Die `IEnumUnknown` Enumerationsschnittstelle ist viel effizienter zum Durchlaufen der Tabelleninhalte als die [idisierbare:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) -Methode und die [iditable:: Item](../../debugger/debug-interface-access/idiatable-item.md) -Methode.  
  
 Die Interpretation der- `IUnknown` Schnittstelle, die von der- `IDiaTable::Item` Methode oder der-Methode zurückgegeben `Next` wird (im Microsoft. VisualStudio. OLE. Interop-Namespace), hängt vom Typ der Tabelle ab. Wenn die Schnittstelle z. b `IDiaTable` . eine Liste von injizierten Quellen darstellt, `IUnknown` sollte die Schnittstelle für die [idiainjetedsource](../../debugger/debug-interface-access/idiainjectedsource.md) -Schnittstelle abgefragt werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) -Methode oder der [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) -Methode ab.  
  
 Die folgenden Schnittstellen werden mit der-Schnittstelle implementiert (d. h. `IDiaTable` Sie können die- `IDiaTable` Schnittstelle für eine der folgenden Schnittstellen Abfragen):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Beispiel  
 Die erste Funktion, `ShowTableNames` , zeigt die Namen aller Tabellen in der Sitzung an. Die zweite Funktion, `GetTable` , durchsucht alle Tabellen nach einer Tabelle, die eine angegebene Schnittstelle implementiert. Die dritte Funktion, `UseTable` , zeigt, wie die- `GetTable` Funktion verwendet wird.  
  
> [!NOTE]
> `CDiaBSTR` ist eine Klasse, die einen umschließt `BSTR` und automatisch die Freigabe der Zeichenfolge behandelt, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
