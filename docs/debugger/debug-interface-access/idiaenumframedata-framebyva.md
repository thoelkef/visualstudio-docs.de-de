---
title: "IDiaEnumFrameData::frameByVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByVA-Methode"
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt einen Rahmen um virtuelle Adresse \(VA\).  
  
## Syntax  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Parameter  
 virtualAddress  
 \[in\]  VA relevante des Frames.  
  
 Rahmen  
 \[out\]  Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt zurück, das den Rahmen darstellt, auf die die bereitgestellte Adresse enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine Rahmen von Daten die angegebene Adresse übereinstimmt.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)