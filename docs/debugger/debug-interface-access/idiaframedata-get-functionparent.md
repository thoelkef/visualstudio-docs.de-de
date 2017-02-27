---
title: "IDiaFrameData::get_functionParent | Microsoft Docs"
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
  - "IDiaFrameData::get_functionParent-Methode"
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_functionParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Rahmen bezugspunkt Oberfläche für die einschließende Funktion ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_functionParent (   
   IDiaFrameData** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt für die einschließende Funktion zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)