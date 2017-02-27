---
title: "IDiaSymbol::get_virtualBasePointerOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualBasePointerOffset-Methode"
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualBasePointerOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Offset des virtuellen niedrigen Zeigertyps ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Offset des virtuellen niedrigen Zeigers zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)