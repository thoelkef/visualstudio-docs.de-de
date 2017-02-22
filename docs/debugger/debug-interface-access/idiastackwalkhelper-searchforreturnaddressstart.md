---
title: "IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs"
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
  - "IDiaStackWalkHelper::searchForReturnAddressStart-Methode"
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sucht den angegebenen Stapelrahmen für eine Rückgabeadresse nah an der angegebenen Stapeladresse.  
  
## Syntax  
  
```cpp#  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### Parameter  
 `frame`  
 \[in\]  Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt, das den aktuellen Stapelrahmen darstellt.  
  
 `startAddress`  
 \[in\]  Von der eine virtuelle Speicheradresse, an dem die Suche beginnen soll.  
  
 `ReturnAddress`  
 \[out\]  Gibt die nächste Funktion rückgabeadresse zu `startAddress`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)