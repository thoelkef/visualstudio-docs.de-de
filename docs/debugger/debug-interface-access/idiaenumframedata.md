---
title: "IDiaEnumFrameData | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData-Schnittstelle"
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Rahmen datenelemente auf, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumFrameData : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumFrameData`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumFrameData::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Ruft die `IEnumVARIANT Interface`\-Version dieses Enumerators ab.|  
|[IDiaEnumFrameData::get\_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Ruft die Anzahl von Rahmen datenelementen ab.|  
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Ruft ein Rahmen datenelement mithilfe eines Indexes ab.|  
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Ruft eine angegebene Anzahl von Rahmen datenelemente in der Enumerationsfolge ab.|  
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Überspringt eine angegebene Anzahl von Rahmen datenelemente in der Enumerationsfolge.|  
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Gibt einen Rahmen um relative virtuelle Adresse \(RVA\).|  
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Gibt einen Rahmen um virtuelle Adresse \(VA\).|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle in der [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)\-Methode.  Weitere Informationen finden Sie im Beispiel für Details.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `GetEnumFrameData` erhält \(Funktion\) und \( `ShowFrameData` die Funktion\) `IDiaEnumFrameData`\-Schnittstelle verwendet.  Zeigen Sie die [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Schnittstelle als ein Beispiel für die `PrintFrameData`\-Funktion.  
  
```cpp#  
  
      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pUnknown    = NULL;  
    REFIID             iid         = __uuidof(IDiaEnumFrameData);  
    IDiaEnumTables*    pEnumTables = NULL;  
    IDiaTable*         pTable      = NULL;  
    ULONG              celt        = 0;  
  
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
  
void ShowFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;  
  
    if (pEnumFrameData != NULL)  
    {  
        IDiaFrameData* pFrameData;  
        ULONG celt = 0;  
  
        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintFrameData(pFrameData);  
            pFrameData->Release();  
        }  
        pEnumFrameData->Release();   
    }  
}  
```  
  
## Anforderungen  
 **Header:** Dia2.h  
  
 **Bibliothek:** diaguids.lib  
  
 **DLLs:** msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)