---
title: "IDiaEnumInjectedSources::Item | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Item-Methode"
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine eingefügte Quelle mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)\-Objekts.  Der Index ist der Bereich von 0 bis \-1, wobei `count``count` von der [IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)\-Methode zurückgegeben wird.  
  
 injectedSource  
 \[out\]  Gibt ein [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)\-Objekt zurück, das die eingefügte Quelle darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)