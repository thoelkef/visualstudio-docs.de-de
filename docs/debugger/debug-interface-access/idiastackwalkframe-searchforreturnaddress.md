---
title: "IDiaStackWalkFrame::searchForReturnAddress | Microsoft Docs"
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
  - "IDiaStackWalkFrame::searchForReturnAddress-Methode"
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkFrame::searchForReturnAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sucht den angegebenen Stapelrahmen für die nächste Funktion rückgabeadresse.  
  
## Syntax  
  
```cpp#  
HRESULT searchForReturnAddress (   
   IDiaFrameData* frame,  
   ULONGLONG*     returnAddress  
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
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)