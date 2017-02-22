---
title: "IDiaEnumDebugStreamData::Skip | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Skip-Methode"
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl von Datensätzen in einer aufgelisteten Sequenz.  
  
## Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der in der aufgelisteten Sequenz zu überspringen, Datensätzen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück, wenn keine weiteren zu überspringen, Datensätze vorhanden sind.  
  
## Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)