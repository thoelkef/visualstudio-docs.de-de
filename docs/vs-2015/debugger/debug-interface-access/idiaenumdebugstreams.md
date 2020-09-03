---
title: Idiaenumdebug-Streams | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams interface
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b56170ce1551f4443d511d4b6fde6c5d177d9c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182515"
---
# <a name="idiaenumdebugstreams"></a>IDiaEnumDebugStreams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Listet die verschiedenen debugstreams auf, die in der Datenquelle enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaEnumDebugStreams` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaEnumDebugStreams::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreams-get-newenum.md)|Ruft die `IEnumVARIANT` Version dieses Enumerators ab.|  
|[IDiaEnumDebugStreams::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Ruft die Anzahl der debugdatenströme ab.|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Ruft einen debugdatenstrom mithilfe eines Indexes ab.|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Ruft eine angegebene Anzahl von debugstreams in der enumerationssequenz ab.|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Überspringt eine angegebene Anzahl von debugstreams in einer enumerationssequenz.|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der Inhalt der debugdatenströme ist implementierungsabhängig, und die Datenformate sind nicht dokumentiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie die [IDiaSession:: getenenumdebugstreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md) -Methode auf, um ein- `IDiaEnumDebugStreams` Objekt abzurufen.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie auf die von dieser Schnittstelle verfügbaren Datenströme zugreifen können. Eine Implementierung der-Funktion finden Sie unter [idiaenumdebug bugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) -Schnittstelle `PrintStreamData` .  
  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)
