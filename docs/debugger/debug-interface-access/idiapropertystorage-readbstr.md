---
title: "IDiaPropertyStorage::ReadBSTR | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBSTR"
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest `BSTR`\-Werte in einem Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Bezeichner der zu lesenden Eigenschaft \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `pValue`  
 \[out\]  Gibt den Eigenschaftswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `BSTR`ist.  
  
## Hinweise  
 `BSTR` wird vom Fenster als mit 0 Zeichenfolge mit Breitzeichen definiert.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)