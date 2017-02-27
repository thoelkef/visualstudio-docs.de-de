---
title: "IDiaSectionContrib::get_nopad | Microsoft Docs"
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
  - "IDiaSectionContrib::get_nopad-Methode"
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSectionContrib::get_nopad
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob der Grenze Speicherplatz zur nächsten Abschnitt nicht aufgefüllt werden soll.  
  
## Syntax  
  
```cpp#  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn der Abschnitt nicht zur nächsten Speicherplatz aufgefüllt wird, gebunden ist Andernfalls wird `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Dies ist eine Eigenschaft, die in der Regel nur auf älteren Dateien angezeigt wird.  
  
## Siehe auch  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)