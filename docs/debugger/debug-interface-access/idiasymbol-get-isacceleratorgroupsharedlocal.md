---
title: "IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs"
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
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob das Symbol zu einer Gruppe freigegebenen lokalen Variable im Code entspricht, der Zugriffstaste für AMP in C\+\+ kompiliert wird.  
  
## Syntax  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### Parameter  
 `pFlag`  
 \[out\] Ein Zeiger auf `BOOL`, der angibt, ob das Symbol in einer Gruppe freigegebenen lokalen Variable im Code entspricht, der Zugriffstaste für AMP in C\+\+ kompiliert wird.  Wenn `TRUE`, `get_baseDataSlot` und `get_baseDataOffset`\-Methoden verwendet werden können, um die Speicherortinformationen für die Variable abzurufen.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)