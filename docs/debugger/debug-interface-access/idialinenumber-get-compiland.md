---
title: "IDiaLineNumber::get_compiland | Microsoft Docs"
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
  - "IDiaLineNumber::get_compiland-Methode"
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Verweis auf das Symbol für die Kompiliereinheit ab, die die Bytes Bild von Text beitrug.  
  
## Syntax  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parameter  
 pRetVal  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt für die Kompiliereinheit zurück, die die Bytes Bild von Text beitrug.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)