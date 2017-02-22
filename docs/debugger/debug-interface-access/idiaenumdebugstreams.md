---
title: "IDiaEnumDebugStreams | Microsoft Docs"
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
  - "IDiaEnumDebugStreams-Schnittstelle"
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Streams Debuggen auf, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumDebugStreams`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumDebugStreams::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreams-get-newenum.md)|Ruft die `IEnumVARIANT`\-Version dieses Enumerators ab.|  
|[IDiaEnumDebugStreams::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Ruft die Anzahl der Debug\- Streams ab.|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Ruft einen Stream Debuggen mithilfe eines Indexes ab.|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Ruft eine angegebene Anzahl von Streams in der Enumerationsfolge ab.|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Überspringt eine angegebene Anzahl von Streams in der Enumerationsfolge.|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
 Der Inhalt von Streams ist Implementierung abhängige Datei Debuggen und Datenformate werden nicht dokumentiert.  
  
## Hinweise für Aufrufer  
 Rufen Sie die [IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)\-Methode zum Abrufen eines `IDiaEnumDebugStreams`\-Objekt.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die Streams zugegriffen wird, die von dieser Schnittstelle zur Verfügung stehen.  Zeigen Sie die [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)\-Schnittstelle für eine Implementierung `PrintStreamData` zu arbeiten.  
  
```cpp#  
void DumpAllDebugStreams( IDiaSession* pSession)  
{  
    IDiaEnumDebugStreams* pEnumStreams;  
  
    wprintf(L"\n\n*** DEBUG STREAMS\n\n");  
    // Retrieve an enumerated sequence of debug data streams  
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)  
    {  
        IDiaEnumDebugStreamData* pStream;  
        ULONG celt = 0;  
  
        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)  
        {  
            PrintStreamData(pStream);  
            pStream->Release();  
        }  
        pEnumStreams->Release();  
    }  
    else  
    {  
      wprintf(L"Failed to get any debug streams!\n");  
    }  
    wprintf(L"\n");  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)