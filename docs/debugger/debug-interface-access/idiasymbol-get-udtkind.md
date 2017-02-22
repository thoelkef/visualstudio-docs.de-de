---
title: "IDiaSymbol::get_udtKind | Microsoft Docs"
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
  - "IDiaSymbol::get_udtKind-Methode"
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Auswahl eines benutzerdefinierten Typs \(UDT\).  
  
## Syntax  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Wert aus der [UdtKind\-Enumeration](../../debugger/debug-interface-access/udtkind.md)\-Enumeration zurück, die die Art eines UDT angegeben wird: Klasse, Struktur oder Union.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind\-Enumeration](../../debugger/debug-interface-access/udtkind.md)