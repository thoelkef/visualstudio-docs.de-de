---
title: "IDiaFrameData::get_type | Microsoft Docs"
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
  - "IDiaFrameData::get_type-Methode"
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ des Rahmens compilerspezifisch ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [StackFrameTypeEnum\-Enumeration](../../debugger/debug-interface-access/stackframetypeenum.md)\-Enumeration zurück, die den Typ des Rahmens compilerspezifisch angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum\-Enumeration](../../debugger/debug-interface-access/stackframetypeenum.md)