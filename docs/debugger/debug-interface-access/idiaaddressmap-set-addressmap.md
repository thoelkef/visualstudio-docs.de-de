---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap-Methode"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt eine Adressumsetzung zum Unterstützen von übersetzungen Lay\-out Bild bereit.  
  
## Syntax  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Parameter  
 `cbData`  
 \[in\]  Die Anzahl der Elemente im `data`\-Parameter.  
  
 `data[]`  
 \[in\]  Ein Array [DiaAddressMapEntry Structure](../../debugger/debug-interface-access/diaaddressmapentry.md) Strukturen, die die Übersetzungs Definition zugeordnet.  
  
 `imagetoSymbols`  
 \[in\]  `TRUE` , wenn der `data`\-Parameter eine Karte aus dem neuen Bildlayout auf das ursprüngliche Lay\-out definiert \(wie durch die Programmdebuginformationen Symbole beschrieben\).  `FALSE` ,  wenn `data` eine Karte zum neuen Bildlayout ist, das vom ursprünglichen Lay\-out übernommen wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Normalerweise ruft der Durchmesser Adressenumwandlungs ist von der Programmdatenbankdatei \(.pdb\) ab.  Wenn diese Werte fehlen, wird die [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)\-Methode zweimal, einmal mit dem `imagetoSymbols`\-Parameter aufgerufen, der an `TRUE` festgelegt ist und ein anderes Mal mit dem `imagetoSymbols`\-Parameter, der auf `FALSE`festgelegt ist.  Adressumsetzungs übersetzungen können nicht mit der [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)\-Methode aktiviert werden, es sei denn, beide Übersetzungs ist zur Verfügung gestellt werden.  
  
## Siehe auch  
 [DiaAddressMapEntry Structure](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)