---
title: "IDiaEnumSegments::Clone | Microsoft Docs"
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
  - "IDiaEnumSegments::Clone-Methode"
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### Parameter  
 ppenum  
 \[out\]  Gibt ein [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)\-Objekt zurück, das ein Duplikat des Enumerators enthält.  Die Segmente werden, wird nur der Enumerator nicht dupliziert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)