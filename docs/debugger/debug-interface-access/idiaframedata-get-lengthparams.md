---
title: "IDiaFrameData::get_lengthParams | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthParams-Methode"
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_lengthParams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl von Bytes Parametern ab, die auf dem Stapel abgelegt werden.  
  
## Syntax  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Anzahl der Bytes Parametern zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der von dieser Methode zurückgegeben wird, wird in der Regel bei der Interpretation einer Zeichenfolge Programm verwendet wird \(siehe [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)\-Methode für die Definition einer Zeichenfolge des Programms\).  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)