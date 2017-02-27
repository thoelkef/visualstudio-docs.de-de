---
title: "IDiaStackWalkFrame::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkFrame::put_registerValue-Methode"
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt den Wert eines Registers festgelegt.  
  
## Syntax  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Ein Wert aus der [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)\-Enumeration, der das Register angibt, in die geschrieben werden soll.  
  
 `NewVal`  
 \[in\]  Der neue Wert des Registers.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)