---
title: "IDiaEnumFrameData::Item | Microsoft Docs"
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
  - "IDiaEnumFrameData::Item-Methode"
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Rahmen datenelement mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekts.  Der Index ist `count`im Bereich von 0 bis \-1, wobei `count` von der [IDiaEnumFrameData::get\_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)\-Methode zurückgegeben wird.  
  
 Abschnitt  
 \[out\]  Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt zurück, das das gewünschte Rahmen datenelement darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)