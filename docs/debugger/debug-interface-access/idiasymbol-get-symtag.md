---
title: "IDiaSymbol::get_symTag | Microsoft Docs"
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
  - "IDiaSymbol::get_symTag-Methode"
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_symTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ des Symbols klassifizierung ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_symTag (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt Ein Wert aus der Enumeration zurück, die die [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Typ von Symbol klassifizierung angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Beispiel  
  
```cpp#  
IDiaSymbol* pType;  
DWORD       tag = 0;  
pType->get_symTag( &tag );  
```  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)