---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest `LONG`\-Werte in einem Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Bezeichner der zu lesenden Eigenschaft \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `pValue`  
 \[out\]  Gibt den Eigenschaftswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `LONG`ist.  
  
## Hinweise  
 `LONG` wird von Windows als 32\-Bit\-Ganzzahl mit Vorzeichen definiert.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)