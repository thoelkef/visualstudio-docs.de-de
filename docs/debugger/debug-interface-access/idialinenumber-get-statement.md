---
title: "IDiaLineNumber::get_statement | Microsoft Docs"
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
  - "IDiaLineNumber::get_statement-Methode"
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag, dass die Zeileninformationen den Anfang einer Anweisung beschrieben wird, anstatt ein Ausdruck, bei der Programmierung Quelle ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn diese Zeileninformationen den Anfang einer Anweisung in der Quelle des Programms beschrieben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Anweisungen können mehrere Zeilen umfassen.  Diese Methode gibt an, ob die zugeordnete Zeilennummer des Anfangs einer solchen mehrzeiligen Statement markiert.  
  
## Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)