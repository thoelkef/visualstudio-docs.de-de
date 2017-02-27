---
title: "IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs"
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
  - "IDiaSymbol::get_optimizedCodeDebugInfo-Methode"
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_optimizedCodeDebugInfo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion Debuginformationen enthält, die für optimierten Code bestimmt ist.  
  
## Syntax  
  
```cpp  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### Parameter  
 `pFlag`  
 \[out\] Gibt `TRUE` zurück, wenn die optimierte Funktion oder die Bezeichnung Debuginformationen enthält; andernfalls `FALSE`.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Description|  
|-----------------|-----------------|  
|Header:|dia2.h|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)