---
title: "IDiaEnumTables::Next | Microsoft Docs"
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
  - "IDiaEnumTables::Next-Methode"
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Tabellen in der Enumerationsfolge ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der Tabellen im Enumerator abgerufen werden sollen.  
  
 `rgelt`  
 \[out\]  Ein Array, das den [IDiaTable](../../debugger/debug-interface-access/idiatable.md)\-Objekten gefüllt werden soll, die die gewünschte Tabelle darstellen.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der abgerufenen Tabellen im Enumerator zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine weiteren Tabellen vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)