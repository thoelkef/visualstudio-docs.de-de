---
title: "IDiaSymbol::get_baseDataSlot | Microsoft Docs"
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
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_baseDataSlot
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den grundlegenden Datenslot ab.  
  
## Syntax  
  
```cpp  
HRESULT get_baseDataSlot(   
   DWORD* pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `DWORD`, der den grundlegenden Datenslot enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)