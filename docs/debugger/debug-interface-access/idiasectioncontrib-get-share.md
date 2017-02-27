---
title: "IDiaSectionContrib::get_share | Microsoft Docs"
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
  - "IDiaSectionContrib::get_share-Methode"
ms.assetid: 05c4c896-4419-4166-8bb2-8d0934dc14b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_share
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob der Bereich im Arbeitsspeicher freigegeben werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT get_share (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn der Abschnitt im Arbeitsspeicher gemeinsam ist. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)