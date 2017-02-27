---
title: "IDiaImageData::get_imageBase | Microsoft Docs"
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
  - "IDiaImageData::get_imageBase-Methode"
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Speicheradresse ab, in der das Bild basieren soll.  
  
## Syntax  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den vorgeschlagenen Bild basiswert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Aufgrund der Seite Bild Konflikten kann ein Bild automatisch mit einer nicht verwendeten Speicherplatz rebased, wenn es geladen wird.  Diese Methode gibt den niedrigen Hinweis zurück \(vorgeschlagene Speicheradresse\), die im Modul zur Kompilierzeit gespeichert wurde.  
  
## Siehe auch  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)