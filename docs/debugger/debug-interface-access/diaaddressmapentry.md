---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry-Enumeration"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Beschreibt einen Eintrag in einer Adressumsetzung.  
  
## Syntax  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elements  
 `rva`  
 Eine relative virtuelle Adresse \(RVA\) im Image A.  
  
 `rvaTo`  
 Die relative virtuelle Adresse `rva` wird in dem Bild B verknüpft.  
  
## Hinweise  
 Eine Adressumsetzung stellt eine Übersetzung von einem Bildlayout \(A\) zu einem anderen \(B\) bereit.  Ein Array von Strukturen `DiaAddressMapEntry``rva` definiert eine sortierte Adressumsetzung.  
  
 Um eine Adresse, führen `addrA`Bild in A auf eine Adresse zu übersetzen. `addrB`, im Bild B, die folgenden Schritte aus:  
  
1.  Suchen Sie die Zuordnung für den Eintrag `e`, mit der größten `rva` kleiner oder gleich `addrA`.  
  
2.  Legen Sie `delta = addrA – e.rva`fest.  
  
3.  Legen Sie `addrB = e.rvaTo + delta`fest.  
  
 Ein Array von Strukturen `DiaAddressMapEntry`[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) wird an die Methode übergeben.  
  
## Anforderungen  
 Header: dia2.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)