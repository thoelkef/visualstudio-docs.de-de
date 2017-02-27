---
title: "IDiaSymbol::get_noReturn | Microsoft Docs"
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
  - "IDiaSymbol::get_noReturn-Methode"
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_noReturn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion gekennzeichnet wurde, z. B. zurückkehrend nie, mit dem [noreturn](/visual-cpp/cpp/noreturn)\-Attribut.  
  
## Syntax  
  
```cpp  
HRESULT get_noReturn(  
   BOOL *pFlag  
);  
```  
  
#### Parameter  
 pFlag  
 \[out\]  Gibt `TRUE` zurück, wenn die Funktion deklariert wurde, z. B. zurückkehrend nie, mit dem `noreturn`\-Attribut. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noreturn](/visual-cpp/cpp/noreturn)