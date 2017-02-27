---
title: "IDiaEnumDebugStreamData | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData-Schnittstelle"
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ermöglicht den Zugriff auf Datensätze in einem Debugbuild Stream.  
  
## Syntax  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumDebugStreamData`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumDebugStreamData::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Ruft die [IEnumVARIANT Interface](http://msdn.microsoft.com/de-de/139e3c93-faef-4003-9079-e0e94494db3e)\-Version dieses Enumerators ab.|  
|[IDiaEnumDebugStreamData::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Ruft die Anzahl der Datensätze Debug Stream ab.|  
|[IDiaEnumDebugStreamData::get\_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Ruft den Namen des Debuggen von Streams ab.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Ruft den angegebenen Datensatz ab.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Ruft die angegebene Anzahl von Datensätzen aus der aufgelisteten Sequenz ab.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Überspringt eine angegebene Anzahl von Datensätzen in einer aufgelisteten Sequenz.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Setzt die aufgelistete Sequenz auf den Anfang zurück.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Erstellt einen Enumerator, der die aufgelistete gleichen Reihenfolge wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
 Diese Schnittstelle stellt einen Datenstrom von Datensätzen in einem Debugbuild Stream dar.  Die Größe und die Interpretation jedes Datensatzes ist vom Stream ab, den der Datensatz von stammt.  Diese Schnittstelle ermöglicht den Zugriff auf effiziente Weise Rohdatenen für Symboldateien in Bytes.  
  
## Hinweise für Aufrufer  
 Rufen Sie die [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) oder Methoden zum Abrufen eines `IDiaEnumDebugStreamData`\-Objekt.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie Sie einen einzigen Stream und ihre Datensätze zugreifen.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)