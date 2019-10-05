---
title: IDiaImageData | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54d09a037fff08b1c34f9a0b5e1fbf018cd10bc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161399"
---
# <a name="idiaimagedata"></a>IDiaImageData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt die Details der Basis Position und Offsets dieses Moduls oder dieser Images an.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaImageData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaImageData`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Ruft die Position im virtuellen Arbeitsspeicher des Moduls relativ zur Anwendung ab.|  
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Ruft die Position im virtuellen Arbeitsspeicher des Bilds ab.|  
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Ruft die Speicheradresse, in dem das Abbild basieren soll.|  
  
## <a name="remarks"></a>Hinweise  
 Einige Debug-Streams (XDATA, PDATA) enthalten, Kopien der Daten, die auch in das Abbild gespeichert wird. Diese Streamen von Daten, die Objekte können, für abgefragt werden die `IDiaImageData` Schnittstelle. Finden Sie im Abschnitt "Hinweise für Aufrufer" in diesem Thema.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch den Aufruf `QueryInterface` auf eine [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) Objekt. Beachten Sie, die nicht alle Debuggen streamt die Unterstützung der `IDiaImageData` Schnittstelle. Beispielsweise derzeit nur die XDATA und PDATA-Streams unterstützen die `IDiaImageData` Schnittstelle.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel durchsucht alle Datenströme Debuggen für alle Datenstrom, unterstützt die `IDiaImageData` Schnittstelle. Wenn es sich bei solchen Datenstrom gefunden wird, ist einige Informationen über den Stream angezeigt.  
  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
