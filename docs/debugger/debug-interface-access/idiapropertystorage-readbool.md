---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest `BOOL`\-Werte in einem Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Bezeichner der zu lesenden Eigenschaft \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `pValue`  
 \[out\]  Gibt den Eigenschaftswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `BOOL`ist.  
  
## Hinweise  
 Für eine konsistente Ergebnisse interpretieren Sie den `BOOL`\-Wert, sodass `TRUE`\-Werte ungleich 0 \(null\) und `FALSE`ist.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)