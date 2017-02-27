---
title: "IDiaLineNumber::get_sourceFile | Microsoft Docs"
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
  - "IDiaLineNumber::get_sourceFile-Methode"
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_sourceFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Verweis auf die Quelldatei ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_sourceFile (   
   IDiaSourceFile** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekt zurück, das die Quelldatei darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)