---
title: "IDiaEnumFrameData::frameByRVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByRVA-Methode"
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt einen Rahmen um relative virtuelle Adresse \(RVA\).  
  
## Syntax  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Parameter  
 relativeVirtualAddress  
 \[in\]  RVA des Rahmens des betroffenen.  
  
 Rahmen  
 \[out\]  Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt zurück, das den Rahmen darstellt, auf die die bereitgestellte Adresse enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine Rahmen von Daten die angegebene Adresse übereinstimmt.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)