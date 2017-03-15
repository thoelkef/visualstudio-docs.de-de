---
title: "IDiaEnumFrameData::Next | Microsoft Docs"
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
  - "IDiaEnumFrameData::Next-Methode"
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Rahmen datenelemente in der Enumerationsfolge ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl von Rahmen datenelementen im Enumerator abgerufen werden sollen.  
  
 rgelt  
 \[out\]  Ein Array mit den angeforderten Rahmen datenelementen ausgefüllt werden [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekten.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl von Rahmen datenelementen im abgerufenen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Datensätze vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)