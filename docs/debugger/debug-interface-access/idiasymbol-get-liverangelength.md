---
title: "IDiaSymbol::get_liveRangeLength | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeLength"
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_liveRangeLength
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Länge des Adressbereichs zurück, in dem das lokale Symbol gültig ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### Parameter  
 `length`  
 \[out\]  Gibt die Länge des Adressbereichs zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein zurückgegebener Fehlercode bedeutet, dass das Symbol nicht aktive Bereichs Informationen verfügt.  
  
## Hinweise  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)