---
title: "IDiaSymbol::get_baseSymbol | Microsoft Docs"
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
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_baseSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft das Symbol ab, von dem der Zeiger basiert.  
  
## Syntax  
  
```cpp  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf das Symbol, von dem der Zeiger basiert.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)