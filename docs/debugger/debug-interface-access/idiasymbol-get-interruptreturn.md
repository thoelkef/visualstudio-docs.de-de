---
title: "IDiaSymbol::get_interruptReturn | Microsoft Docs"
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
  - "IDiaSymbol::get_interruptReturn-Methode"
ms.assetid: 9665da6c-4cc0-41d7-b2e2-0d9e50174cf8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_interruptReturn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion eine Rückgabe von der Unterbrechungsanweisung enthält \(z. B. den X86\-Assemblycode `iret`\).  
  
## Syntax  
  
```cpp  
HRESULT get_interruptReturn(  
   BOOL *pFlag  
);  
```  
  
#### Parameter  
 `pFlag`  
 \[out\]  Gibt `TRUE` zurück, wenn die Funktion eine Rückgabe von der Unterbrechungsanweisung enthält. andernfalls gibt `FALSE`zurück.  
  
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