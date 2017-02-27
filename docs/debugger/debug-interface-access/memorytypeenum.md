---
title: "MemoryTypeEnum | Microsoft Docs"
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
  - "MemoryTypeEnum-Enumeration"
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# MemoryTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Typ des Speichers an, um zuzugreifen.  
  
## Syntax  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### Parameter  
 `MemTypeCode`  
 Nur der den Code zugreift.  
  
 `MemTypeData`  
 Zugreifen auf Daten oder den Stapel.  
  
 `MemTypeStack`  
 Stapel der Speicher nur zugreift.  
  
 `MemTypeAny`  
 Greift auf eine beliebige Art von Arbeitsspeicher zu.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden zur [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)\-Methode zum Zugriff auf verschiedene Typen von Arbeitsspeicher übergeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)