---
title: "IDiaSymbol::get_symIndexId | Microsoft Docs"
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
  - "IDiaSymbol::get_symIndexId-Methode"
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_symIndexId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den eindeutigen Bezeichner des Symbols ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT get_symIndexId (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Symbol ID des Symbols zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Der Bezeichner ist ein eindeutiger Wert, der vom DIA SDK erstellt wird, um alle Symbole zu markieren, wie eindeutig.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)