---
title: "IDiaSymbol::get_memorySpaceKind | Microsoft Docs"
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
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_memorySpaceKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Speicherbereichsart ab.  
  
## Syntax  
  
```cpp  
HRESULT get_memorySpaceKind(   
   DWORD* pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `DWORD`, der den Speicherbereich enthält enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)