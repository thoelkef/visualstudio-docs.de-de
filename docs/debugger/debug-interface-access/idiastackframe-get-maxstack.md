---
title: "IDiaStackFrame::get_maxStack | Microsoft Docs"
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
  - "IDiaStackFrame::get_maxStack-Methode"
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_maxStack
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
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn die Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)