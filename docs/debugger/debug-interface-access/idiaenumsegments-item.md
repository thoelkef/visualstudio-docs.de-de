---
title: "IDiaEnumSegments::Item | Microsoft Docs"
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
  - "IDiaEnumSegments::Item-Methode"
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Segment mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)\-Objekts.  Der Index ist `count`im Bereich von 0 bis \-1, wobei `count` von der [IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)\-Methode zurückgegeben wird.  
  
 Segment  
 \[out\]  Gibt ein [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)\-Objekt zurück, das das gewünschte Segment darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)