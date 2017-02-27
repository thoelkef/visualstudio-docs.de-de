---
title: "IDiaFrameData::get_virtualAddress | Microsoft Docs"
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
  - "IDiaFrameData::get_virtualAddress-Methode"
ms.assetid: de137bee-132f-4aae-a067-9578b7a3e6d4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die virtuelle Adresse \(VA\) des Codes für den Zielframe ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die virtuelle Adresse des Codes für die Frames zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)