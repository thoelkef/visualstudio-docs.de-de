---
title: "IDiaEnumSectionContribs::Next | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Next-Methode"
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl Abschnitt stellt in der Enumerationsfolge ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parameter  
 Celt  
 \[in\]  Die Anzahl der Abschnitt abgerufen werden soll beiträgen im Enumerator.  
  
 rgelt  
 \[out\]  Ein Array, das den [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)\-Objekten gefüllt werden soll, die die gewünschten Abschnitt stellt darstellen.  
  
 pceltFetched  
 \[out\]  Gibt die Anzahl der abgerufenen im Abschnitt beiträgen Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Abschnitt stellt vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)