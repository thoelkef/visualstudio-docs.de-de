---
title: "IDiaSymbol::get_language | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_language-Methode"
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_language
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Sprache der Quelle ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [CV\_CFL\_LANG\-Enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md)\-Enumeration zurück, der die Sprache der Quelle angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CFL\_LANG\-Enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md)