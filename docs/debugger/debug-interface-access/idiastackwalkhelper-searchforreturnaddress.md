---
title: "IDiaStackWalkHelper::searchForReturnAddress | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::searchForReturnAddress-Methode"
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::searchForReturnAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sucht den angegebenen Stapelrahmen für die nächste Funktion rückgabeadresse.  
  
## Syntax  
  
```cpp#  
HRESULT searchForReturnAddress(   
   IDiaFrameData*  frame,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### Parameter  
 `frame`  
 \[in\]  Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt, das den aktuellen Stapelrahmen darstellt.  
  
 `returnAddress`  
 \[out\]  Gibt die nächste Funktion rückgabeadresse zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)