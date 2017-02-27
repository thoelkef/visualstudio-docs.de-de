---
title: "IDiaSymbol::get_isPointerToDataMember | Microsoft Docs"
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
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerToDataMember
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt an, ob dieses Symbol ein Zeiger auf einen Datenmember ist.  
  
## Syntax  
  
```cpp  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `BOOL`, der angibt, ob dieses Symbol ein Zeiger auf einen Datenmember ist.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)