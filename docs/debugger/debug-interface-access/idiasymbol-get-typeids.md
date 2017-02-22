---
title: "IDiaSymbol::get_typeIds | Microsoft Docs"
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
  - "IDiaSymbol::get_typeIds-Methode"
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Array von compilerspezifischen Typ\-Bezeichner Attributwerte für dieses Symbol ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### Parameter  
 `cTypeIds`  
 \[in\]  Größe des Puffers, in dem die Daten enthält.  
  
 `pcTypeIds`  
 \[out\]  Gibt die Anzahl der geschriebenen `typeIds` oder wenn `typeIds``NULL`ist, ist die Gesamtzahl der verfügbaren Typ Bezeichnern zurück.  
  
 `typeIds[]`  
 \[out\]  Ein Array, das den Typ Bezeichnern gefüllt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)