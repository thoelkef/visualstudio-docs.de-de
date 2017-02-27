---
title: "IDiaEnumSectionContribs | Microsoft Docs"
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
  - "IDiaEnumSectionContribs-Schnittstelle"
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSectionContribs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Abschnitt stellt ein, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumSectionContribs`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumSectionContribs::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Ruft die [IEnumVARIANT Interface](http://msdn.microsoft.com/de-de/139e3c93-faef-4003-9079-e0e94494db3e)\-Version dieses Enumerators ab.|  
|[IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|Ruft die Anzahl der beiträgen Abschnitt ab.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Ruft Abschnitt stellt mithilfe eines Indexes ab.|  
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|Ruft eine angegebene Anzahl Abschnitt stellt in der Enumerationsfolge ab.|  
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|Überspringt eine angegebene Anzahl Abschnitt stellt in der Enumerationsfolge.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
  
## Hinweis für Aufrufer  
 Rufen Sie diese Schnittstelle in der [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)\-Methode.  Weitere Informationen finden Sie im Beispiel für Details.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `GetEnumSectionContribs` erhält \(Funktion\) und \( `ShowSectionContribs` die Funktion\) `IDiaEnumSectionContribs`\-Schnittstelle verwendet.  Ein ausführlicheres Beispiel finden, die beiträgen Abschnitts Anwendung von [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)\-Schnittstelle.  
  
```cpp#  
  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)