---
title: "IDiaSymbol::get_access | Microsoft Docs"
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
  - "IDiaSymbol::get_access-Methode"
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_access
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Zugriffsmodifizierer eines Klassenmembers ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)\-Enumeration zurück, die den Zugriffsmodifizierer eines Klassenmembers angegeben wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)