---
title: "IDiaFrameData::get_maxStack | Microsoft Docs"
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
  - "IDiaFrameData::get_maxStack-Methode"
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_maxStack
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die maximale Anzahl von Bytes ab, die in den Frames auf dem Stapel abgelegt werden.  
  
## Syntax  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die maximale Anzahl von Bytes zurück, die auf dem Stapel abgelegt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der von dieser Methode zurückgegeben wird, wird in der Regel bei der Interpretation einer Zeichenfolge Programm verwendet wird \(siehe [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)\-Methode für die Definition einer Zeichenfolge des Programms\).  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)