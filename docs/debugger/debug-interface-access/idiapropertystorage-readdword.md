---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest `DWORD`\-Werte in einem Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Bezeichner der zu lesenden Eigenschaft \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `pValue`  
 \[out\]  Gibt den Eigenschaftswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `DWORD`ist.  
  
## Hinweise  
 `DWORD` wird vom Fenster als 32\-Bit\-Ganzzahl ohne Vorzeichen definiert.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)