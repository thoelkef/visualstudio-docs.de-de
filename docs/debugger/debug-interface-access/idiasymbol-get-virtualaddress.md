---
title: "IDiaSymbol::get_virtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualAddress-Methode"
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die virtuelle Adresse \(VA\) des Speicherorts ab.  Verwenden Sie diese Option, wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) zu `LocIsStatic`festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die virtuelle Adresse des Speicherorts zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)