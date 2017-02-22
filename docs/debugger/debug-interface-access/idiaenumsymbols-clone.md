---
title: "IDiaEnumSymbols::Clone | Microsoft Docs"
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
  - "IDiaEnumSymbols::Clone-Methode"
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### Parameter  
 ppenum  
 \[out\]  Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)\-Objekt zurück, das ein Duplikat des Enumerators enthält.  Die Symbole werden, wird nur der Enumerator nicht dupliziert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)