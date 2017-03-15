---
title: "IDiaSymbol::get_types | Microsoft Docs"
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
  - "IDiaSymbol::get_types-Methode"
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Array von compilerspezifischen Typen für dieses Symbol ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### Parameter  
 `cTypes`  
 \[in\]  Größe des Puffers, in dem die Daten enthält.  
  
 `pcTypes`  
 \[out\]  Gibt die Anzahl der geschriebenen Typen oder wenn der Parameter `types``NULL`ist, ist die Gesamtzahl der verfügbaren Typen zurück.  
  
 `types[]`  
 \[out\]  Ein Array, das den [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekten gefüllt werden soll, die alle Typen für dieses Symbol darstellen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)