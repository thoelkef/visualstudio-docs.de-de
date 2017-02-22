---
title: "IDiaStackWalkFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkFrame::get_registerValue-Methode"
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Wert eines Registers ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Ein Wert aus der [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)\-Enumeration, der das Register angibt, in der der Wert abgerufen werden soll.  
  
 `pRetVal`  
 \[out\]  Gibt den aktuellen Wert des Registers zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)