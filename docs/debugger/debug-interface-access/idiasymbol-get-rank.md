---
title: "IDiaSymbol::get_rank | Microsoft Docs"
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
  - "IDiaSymbol::get_rank-Methode"
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Rang \(Anzahl der Dimensionen\) Fortrans eines mehrdimensionalen Arrays ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Anzahl der Dimensionen in einem mehrdimensionalen Feld Fortrans zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Rang bezeichnet die Anzahl der Dimensionen in einem Array an, in dem das Array als `myarray[1,2,3]`deklariert ist.  In diesem Beispiel verfügt über einen Rang 3 und 3 Dimensionen.  Rangfolge gilt nicht für C\+\+, der das Konzept eines Arrays von Arrays für jede Dimension verwendet \(also `myarray[1][2][3]`\).  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)