---
title: "IDiaSymbol::get_packed | Microsoft Docs"
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
  - "IDiaSymbol::get_packed-Methode"
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_packed
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp \(UDT\) verpackt wird.  
  
## Syntax  
  
```cpp#  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn der UDT verpackt ist. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Gepackt bedeutet, dass alle Member des UDT so zusammen nahes positioniertes sind, z. B. möglich, ohne dazwischenliegende an Arbeitsspeicher begrenzen einen Abstand ausgerichtet.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)