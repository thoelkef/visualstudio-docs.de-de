---
title: "IDiaSymbol::get_baseSymbolId | Microsoft Docs"
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
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_baseSymbolId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Symbol ID ab, von der der Zeiger basiert.  
  
## Syntax  
  
```cpp  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `DWORD`, der die Symbol ID enthält, von der der Zeiger basiert.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)