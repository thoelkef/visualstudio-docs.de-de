---
title: "IDiaEnumInjectedSources::Skip | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Skip-Methode"
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl eingefügte Quellen in der Enumerationsfolge.  
  
## Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der eingefügten Quellen in der Enumerationsfolge zu überspringen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück, wenn keine weiteren eingefügte zu überspringen gibt Quellen.  
  
## Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)