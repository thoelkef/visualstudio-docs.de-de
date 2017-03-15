---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Item-Methode"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den angegebenen Datensatz ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden Datensatzes.  Der Index ist `count`im Bereich von 0 bis \-1, wobei `count` von [IDiaEnumDebugStreamData::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)zurückgegeben wurde.  
  
 cbData  
 \[in\]  Größe in Bytes im Datenpuffer.  
  
 pcbData  
 \[out\]  Gibt die Anzahl der zurückgegebenen Bytes zurück.  Wenn `data``NULL`ist, enthält `pcbData` die Gesamtzahl von Bytes der Daten im angegebenen Datensatz verfügbar sind.  
  
 Daten \[\]  
 \[out\]  Ein Puffer, der den Datensatz Stream Debuggen von Daten gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_INVALIDARG` für ungültige Parameter zurück, wenn der `index`\-Parameter durch Grenzen Bereichs liegt.  
  
## Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)