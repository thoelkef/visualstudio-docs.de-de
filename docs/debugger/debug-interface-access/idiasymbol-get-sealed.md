---
title: "IDiaSymbol::get_sealed | Microsoft Docs"
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
  - "IDiaSymbol::get_sealed-Methode"
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDiaSymbol::get_sealed
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Klasse oder Methode versiegelt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_sealed(   
   BOOL* pRetVal)  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn die Klasse oder Methode versiegelt ist. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Eine versiegelte Klasse kann nicht als Basisklasse verwendet werden.  Eine versiegelte Methode kann nicht overidden sein.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)