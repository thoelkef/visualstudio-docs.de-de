---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest `ULONGLONG`\-Werte in einem Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Bezeichner der zu lesenden Eigenschaft \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `pValue`  
 \[out\]  Gibt den Eigenschaftswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `ULONGLONG`ist.  
  
## Hinweise  
 `ULONGLONG` wird vom Fenster als 64\-Bit\-Ganzzahl ohne Vorzeichen definiert.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)