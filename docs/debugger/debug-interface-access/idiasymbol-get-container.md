---
title: "IDiaSymbol::get_container | Microsoft Docs"
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
  - "IDiaSymbol::get_container-Methode"
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft einen Zeiger auf ein Symbol ab, das das übergeordnete Element bzw. den Container dieses Symbols darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen Zeiger auf `IDiaSymbol` zurück, das Informationen über den Container dieses Symbols enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt S\_FALSE oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein Rückgabewert von S\_FALSE bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)