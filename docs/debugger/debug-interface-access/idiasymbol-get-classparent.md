---
title: "IDiaSymbol::get_classParent | Microsoft Docs"
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
  - "IDiaSymbol::get_classParent-Methode"
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_classParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Verweis auf den Klassen übergeordneten Element des Symbols ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein Objekt zurück, das [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Klassen das übergeordnete Element des Symbols darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Hinweise  
 Die Typen von Symbolen, die Klassen übergeordnete Elemente sein können, werden in [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)dokumentiert.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)