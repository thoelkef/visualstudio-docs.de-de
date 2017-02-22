---
title: "IDiaEnumSectionContribs::Item | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Item-Methode"
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft Abschnitt stellt mithilfe eines Indexes ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### Parameter  
 Index  
 \[in\]  Der Index des abzurufenden [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)\-Objekts.  Der Index ist `count`im Bereich von 0 bis \-1, wobei `count` von der [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)\-Methode zurückgegeben wird.  
  
 Abschnitt  
 \[out\]  Gibt ein [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)\-Objekt zurück, das den gewünschten Bereich beitrag darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)