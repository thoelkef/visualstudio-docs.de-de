---
title: "IDiaSymbol::get_objectFileName | Microsoft Docs"
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
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_objectFileName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Objektdateinamen ab.  
  
## Syntax  
  
```cpp  
HRESULT get_objectFilename(   
   BSTR *pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `BSTR`, der den Objektdateinamen enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)