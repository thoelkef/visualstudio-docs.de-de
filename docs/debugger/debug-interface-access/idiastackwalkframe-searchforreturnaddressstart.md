---
title: "IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs"
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
  - "IDiaStackWalkFrame::searchForReturnAddressStart-Methode"
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sucht den angegebenen Stapelrahmen für eine Rückgabeadresse nah an der angegebenen Adresse.  
  
## Syntax  
  
```cpp#  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### Parameter  
 `frame`  
 \[in\]  Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)\-Objekt, das den aktuellen Stapelrahmen darstellt.  
  
 `startAddress`  
 \[in\]  Von der eine virtuelle Speicheradresse, an dem die Suche beginnen soll.  
  
 `returnAddress`  
 \[out\]  Gibt die nächste Funktion rückgabeadresse zu `startAddress`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)