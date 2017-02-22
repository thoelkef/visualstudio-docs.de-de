---
title: "IDiaAddressMap::get_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::get_imageAlign-Methode"
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die aktuelle Ausrichtung des Bilds ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Wert für das Bild der ausführbaren Datei zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Bilder sind auf bestimmte Arbeitsspeicher begrenzen ausgerichtet, abhängend, wie das Bild geladen und erstellt wurde.  Die Ausrichtung ist in der Regel auf 1, 2, 4, 8, 16, 32 oder 64 Bytes hinweg.  Die Ausrichtung des Bilds kann mit einem Aufruf der [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)\-Methode festgelegt werden.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)