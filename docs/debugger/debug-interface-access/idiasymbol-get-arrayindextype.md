---
title: "IDiaSymbol::get_arrayIndexType | Microsoft Docs"
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
  - "IDiaSymbol::get_arrayIndexType-Methode"
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_arrayIndexType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Symbol Oberfläche des Typs Arrayindex des Symbols ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_arrayIndexType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das den Arrayindex den Typ des Symbols darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Einige Sprachen können den Typ angeben, der als Index in ein Array verwendet wird.  Das Symbol, das von dieser Methode zurückgegeben wird, gibt den Typ an.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)