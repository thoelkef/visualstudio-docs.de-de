---
title: "IDiaEnumLineNumbers::Clone | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Clone-Methode"
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumLineNumbers::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### Parameter  
 `ppenum`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)\-Objekt zurück, das ein Duplikat des Enumerators enthält.  Die Zeilennummern werden nicht, sondern lediglich den Enumerator. dupliziert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)