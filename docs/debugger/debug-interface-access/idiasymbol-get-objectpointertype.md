---
title: "IDiaSymbol::get_objectPointerType | Microsoft Docs"
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
  - "IDiaSymbol::get_objectPointerType-Methode"
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_objectPointerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ des Objektzeigers für eine Klassenmethode ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_objectPointerType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein Objekt zurück, das den [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objektzeiger für eine Klassenmethode darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Diese Eigenschaft gilt nur für Symbole mit einem [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Typ `SymTagFunctionType`.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)