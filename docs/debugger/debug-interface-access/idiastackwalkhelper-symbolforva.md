---
title: "IDiaStackWalkHelper::symbolForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::symbolForVA-Methode"
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft das Symbol ab, das die angegebene virtuelle Adresse enthält.  
  
## Syntax  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### Parameter  
 `va`  
 \[in\]  Die virtuelle Adresse, die im angeforderten Symbol enthalten ist.  Das Symbol muss `SymTagFunctionType` \(ein Wert aus der [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Enumeration\) sein.  
  
 `ppSymbol`  
 \[out\]  Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das das Symbol an der angegebenen Adresse.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)