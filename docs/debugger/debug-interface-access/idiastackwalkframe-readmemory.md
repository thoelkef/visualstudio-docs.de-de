---
title: "IDiaStackWalkFrame::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkFrame::readMemory-Methode"
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest Speicher im Abbild.  
  
## Syntax  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parameter  
 `type`  
 \[in\] Einer der [MemoryTypeEnum\-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)\-Enumerationswerte, der den Typ des Speichers angibt, die zuzugreifen.  
  
 `va`  
 \[in\] virtueller Adressenplatz im Bild, ab dem gelesen werden soll.  
  
 `cbData`  
 \[in\] Größe in Bytes im Datenpuffer.  
  
 `pcbData`  
 \[out\] Gibt die Anzahl der zurückgegebenen Bytes zurück.  Wenn `data``NULL` ist, enthält `pcbData` die Gesamtzahl von Bytes verfügbaren Daten.  
  
 `data`  
 \[out\] Ein Puffer, der vom angegebenen Speicherort mit Daten gefüllt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK` zurück; andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)