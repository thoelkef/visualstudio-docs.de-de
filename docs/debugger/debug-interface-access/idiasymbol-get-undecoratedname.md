---
title: "IDiaSymbol::get_undecoratedName | Microsoft Docs"
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
  - "IDiaSymbol::get_undecoratedName-Methode"
ms.assetid: e49edf25-a51d-4787-bd5b-2bf5af827c8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_undecoratedName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den nicht ergänzten Namen für C oder C\+\+ Bindung, die ergänzten Namen ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_undecoratedName (   
   BSTR* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den nicht ergänzten Namen für die ergänzten Namen in C\-Format \+\+ zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)