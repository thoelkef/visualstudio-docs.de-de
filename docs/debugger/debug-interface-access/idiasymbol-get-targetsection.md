---
title: "IDiaSymbol::get_targetSection | Microsoft Docs"
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
  - "IDiaSymbol::get_targetSection-Methode"
ms.assetid: 95382395-da41-4aa8-87f1-5b03da128565
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_targetSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Adressteil eines Thunkziels ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_targetSection (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Bestandteil einer Thunk \- adresse Ziel.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)