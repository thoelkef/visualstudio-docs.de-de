---
title: "IDiaEnumSourceFiles | Microsoft Docs"
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
  - "IDiaEnumSourceFiles-Schnittstelle"
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Quelldateien auf, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumSourceFiles`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumSourceFiles::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Ruft die `IEnumVARIANT Interface`\-Version dieses Enumerators ab.|  
|[IDiaEnumSourceFiles::get\_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Ruft die Anzahl von Quelldateien ab.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Ruft eine Quelldatei mithilfe eines Indexes ab.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Ruft eine angegebene Anzahl von Quelldateien in der Enumerationsfolge ab.|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Überspringt eine angegebene Anzahl von Quelldateien in der Enumerationsfolge.|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die `QueryInterface`\-Methode für ein [IDiaTable](../../debugger/debug-interface-access/idiatable.md)\-Objekts aufruft.  Weitere Informationen finden Sie im Beispiel für Details.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `IDiaEnumSourceFiles`\-Schnittstelle aus dem Liste der Tabellen in einem Durchmesser\-Sitzungsobjekt abgerufen wird.  Ein Beispiel für den Zugriff auf die Quelldatei Informationen finden Sie in der [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Schnittstelle.  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
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
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)