---
title: "IDiaEnumLineNumbers::Item | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Item-Methode"
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Zeilennummer mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)\-Objekts.  Der Index ist `count`im Bereich von 0 bis \-1, wobei `count` von der [IDiaEnumLineNumbers::get\_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)\-Methode zurückgegeben wird.  
  
 lineNumber  
 \[out\]  Gibt ein [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)\-Objekt zurück, das die gewünschte Zeilennummer darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)