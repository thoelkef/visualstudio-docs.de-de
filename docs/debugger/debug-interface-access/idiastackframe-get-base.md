---
title: "IDiaStackFrame::get_base | Microsoft Docs"
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
  - "IDiaStackFrame::get_base-Methode"
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_base
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Basisadresse des Rahmens ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_base (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Basisadresse zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn die Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)