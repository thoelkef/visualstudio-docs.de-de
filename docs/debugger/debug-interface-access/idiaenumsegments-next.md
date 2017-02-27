---
title: "IDiaEnumSegments::Next | Microsoft Docs"
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
  - "IDiaEnumSegments::Next-Methode"
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl von Segmenten im Enumerator abgerufen werden sollen.  
  
 rgelt  
 \[out\]  Ein Array, das mit den gewünschten [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)\-Objekten gefüllt werden soll, die die Segmente darstellen.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl von Segmenten im abgerufenen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Segmente vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)