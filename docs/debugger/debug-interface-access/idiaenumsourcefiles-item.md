---
title: "IDiaEnumSourceFiles::Item | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Item-Methode"
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Quelldatei mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekts.  Der Index ist `count`im Bereich von 0 bis \-1, wobei`count` von der [IDiaEnumSourceFiles::get\_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)\-Methode zurückgegeben wird.  
  
 sourceFile  
 \[out\]  Gibt ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekt zurück, das die gewünschte Quelldatei darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)