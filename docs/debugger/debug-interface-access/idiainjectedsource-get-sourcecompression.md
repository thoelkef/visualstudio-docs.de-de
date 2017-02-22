---
title: "IDiaInjectedSource::get_sourceCompression | Microsoft Docs"
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
  - "IDiaInjectedSource::get_sourceCompression-Methode"
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_sourceCompression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Zähler der verwendeten Sources komprimierung ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Zähler der verwendeten Sources komprimierung zurück.  Ein Wert von null gibt an, dass keine Sources komprimierung verwendet wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der von dieser Methode zurückgegeben wird, entspricht dem verwendeten Compiler bestimmt.  Zum Beispiel könnte ein Compiler Ausgeführte\-LENGTH Codierung oder Huffman\-Format Komprimierung.  
  
## Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)