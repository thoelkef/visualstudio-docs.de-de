---
title: "IDiaEnumInjectedSources | Microsoft Docs"
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
  - "IDiaEnumInjectedSources-Schnittstelle"
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumInjectedSources
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listen Sie die verschiedenen eingefügten Quellen aufgeführt, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumInjectedSources`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumInjectedSources::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Ruft die [IEnumVARIANT Interface](http://msdn.microsoft.com/de-de/139e3c93-faef-4003-9079-e0e94494db3e)\-Version dieses Enumerators ab.|  
|[IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Ruft die Anzahl der eingefügten Quellen ab.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Ruft eine eingefügte Quelle mithilfe eines Indexes ab.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Ruft eine angegebene Anzahl eingefügte Quellen in der Enumerationsfolge ab.|  
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Überspringt eine angegebene Anzahl eingefügte Quellen in der Enumerationsfolge.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, indem die [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)\-Methode mit dem Namen einer bestimmten Quelldatei aufgerufen wird oder indem die [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)\-Methode mit dem `IDiaEnumInjectedSources` GUID der Schnittstelle aufruft.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `GetEnumInjectedSources` erhält \(Funktion\) und \( `DumpAllInjectedSources` die Funktion\) `IDiaEnumInjectedSources`\-Schnittstelle verwendet.  Zeigen Sie die [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)\-Schnittstelle für eine Implementierung `PrintPropertyStorage` zu arbeiten.  Bei einer Ausgabe Alternativen finden Sie in der [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)\-Schnittstelle.  
  
```cpp#  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
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
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)