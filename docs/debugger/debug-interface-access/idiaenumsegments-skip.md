---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
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
  - "IDiaEnumSegments::Skip-Methode"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl von Segmenten in der Enumerationsfolge.  
  
## Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl von Segmenten in der Enumerationsfolge zu überspringen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück, wenn keine weiteren zu überspringen gibt Segmente.  
  
## Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)