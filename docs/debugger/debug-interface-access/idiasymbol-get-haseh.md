---
title: "IDiaSymbol::get_hasEH | Microsoft Docs"
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
  - "IDiaSymbol::get_hasEH-Methode"
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_hasEH
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion eine nicht verwaltete C\+\+\-style Ausnahmebehandlung enthält \(z. B. ein try\/catch\-Block verwendet\).  
  
## Syntax  
  
```cpp  
HRESULT get_hasEH(  
   BOOL *pFlag  
);  
```  
  
#### Parameter  
 `pFlag`  
 \[out\]  Gibt `TRUE` zurück, wenn die Funktion eine C\+\+\-style Ausnahmebehandlung verfügt. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)