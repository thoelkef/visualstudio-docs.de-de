---
title: "IDiaSegment::get_read | Microsoft Docs"
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
  - "IDiaSegment::get_read-Methode"
ms.assetid: aafbc86d-352c-4e1a-911a-1472d2d59212
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_read
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob das Segment gelesen werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT get_read (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn das Segment gelesen werden kann. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)