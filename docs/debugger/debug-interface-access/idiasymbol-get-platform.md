---
title: "IDiaSymbol::get_platform | Microsoft Docs"
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
  - "IDiaSymbol::get_platform-Methode"
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ der Plattform ab, für den die Kompiliereinheit kompiliert wurde.  
  
## Syntax  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)\-Enumeration zurück, die den Typ von Plattform angibt, auf den die Kompiliereinheit kompiliert wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)