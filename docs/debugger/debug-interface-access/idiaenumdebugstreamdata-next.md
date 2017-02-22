---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next-Methode"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Datensätzen in der aufgelisteten Sequenz ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der abzurufenden Datensätze.  
  
 cbData  
 \[in\]  Größe in Bytes im Datenpuffer.  
  
 pcbData  
 \[out\]  Gibt die Anzahl der zurückgegebenen Bytes zurück.  Wenn `data` NULL ist, enthält `pcbData` die Gesamtzahl von Bytes der Daten, die für alle angeforderten Datensätzen verfügbar sind.  
  
 Daten \[\]  
 \[out\]  Ein Puffer, der den Datensatz Stream Debuggen von Daten gefüllt werden soll.  
  
 pceltFetched  
 \[in, out\]  Gibt die Anzahl der Datensätze in `data`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Datensätze vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)