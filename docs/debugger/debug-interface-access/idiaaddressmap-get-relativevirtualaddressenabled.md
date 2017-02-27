---
title: "IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::get_relativeVirtualAddressEnabled-Methode"
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::get_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt an, ob die Berechnung und der Verwendung von relativen virtuellen Adressen \(RVA\) aktiviert ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 pRetVal  
 \[out\]  Gibt `TRUE` zurück, wenn die Berechnung von RVAs aktiviert ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 RVAs sind aktiviert, wenn zunächst die Segmente aus einer PDB\-Datei geladen wurden.  Die Verwendung von RVAs kann vorübergehend deaktiviert werden, indem die [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)\-Methode aufruft.  
  
 Außerdem können Header des Bilds neue eingerichtet werden, indem die [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)\-Methode wurde, gefolgt von einem Aufruf der `put_relativeVirtualAddressEnabled`\-Methode, um dem RVAs mithilfe der neuen Header des Bilds zu aktivierenden aufruft.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)