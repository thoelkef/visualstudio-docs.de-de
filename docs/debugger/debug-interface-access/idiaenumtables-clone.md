---
title: "IDiaEnumTables::Clone | Microsoft Docs"
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
  - "IDiaEnumTables::Clone-Methode"
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### Parameter  
 `ppenum`  
 \[out\]  Gibt ein [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)\-Objekt zurück, das ein Duplikat des Enumerators enthält.  Die Tabellen sind nur der Enumerator nicht dupliziert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)