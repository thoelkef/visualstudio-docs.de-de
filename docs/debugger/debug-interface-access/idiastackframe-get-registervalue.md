---
title: "IDiaStackFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_registerValue-Methode"
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Wert eines angegebenen Registers ab, wie im Stapelrahmen gespeichert.  
  
## Syntax  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### Parameter  
 `registerIndex`  
 \[in\]  Einer der [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)\-Enumerationswerte.  
  
 `pRetVal`  
 \[out\]  Wert im Register gespeichert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)