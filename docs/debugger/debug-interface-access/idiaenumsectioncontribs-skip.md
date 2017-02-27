---
title: "IDiaEnumSectionContribs::Skip | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Skip-Methode"
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl Abschnitt stellt in der Enumerationsfolge.  
  
## Syntax  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der beiträgen Abschnitts in der Enumerationsfolge auf den Schritt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück, wenn keine weiteren Abschnitt stellt mit Schritt gibt.  
  
## Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)