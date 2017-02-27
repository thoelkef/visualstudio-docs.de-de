---
title: "IDiaFrameData::get_lengthBlock | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthBlock-Methode"
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_lengthBlock
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Länge in Bytes des Codeblocks ab, der durch den Frame beschrieben wird.  
  
## Syntax  
  
```cpp#  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Anzahl der Bytes des Codes in den Frames zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der von dieser Methode zurückgegeben wird, wird in der Regel bei der Interpretation einer Zeichenfolge Programm verwendet wird \(siehe [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)\-Methode für die Definition einer Zeichenfolge des Programms\).  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)