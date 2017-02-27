---
title: "IDiaImageData | Microsoft Docs"
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
  - "IDiaImageData-Schnittstelle"
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaImageData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Macht die Details der Speicherort\- Arbeitsspeicher und Offset des Moduls oder eines Bilds.  
  
## Syntax  
  
```  
IDiaImageData : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaImageData`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaImageData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Ruft die Position im virtuellen Speicher des Moduls relativ zur Anwendung ab.|  
|[IDiaImageData::get\_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Ruft die Position im virtuellen Speicher des Bilds ab.|  
|[IDiaImageData::get\_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Ruft die Speicheradresse ab, in der das Bild basieren soll.|  
  
## Hinweise  
 Einige von Streams \(XDATA und PDATA\) enthalten Kopien der Daten, die auch im Bild gespeichert werden.  Diese Stream datenobjekte können für die `IDiaImageData`\-Schnittstelle abgefragt werden.  Weitere Informationen finden Sie im Abschnitt „Hinweise für Aufrufer“ in diesem Thema.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie `QueryInterface` auf einem [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)\-Objekts aufruft.  Beachten Sie, dass nicht alle Streams unterstützen die `IDiaImageData`\-Schnittstelle debuggen.  Zum Beispiel nur die derzeit XDATA\- und PDATA\-Datenströme unterstützen die `IDiaImageData`\-Schnittstelle.  
  
## Beispiel  
 In diesem Beispiel wird in allen Debuggen von Streams für jeden Datenstrom, der die `IDiaImageData`\-Schnittstelle unterstützt.  Wenn ein solcher Streams gefunden wird, werden einige Informationen über diesen Stream angezeigt.  
  
```cpp#  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)