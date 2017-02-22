---
title: "LocationType | Microsoft Docs"
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
  - "LocationType-Enumeration"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Art von Standortinformationen in einem Symbol an.  
  
## Syntax  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Elements  
 `LocIsNull`  
 Positionsinformationen sind nicht verfügbar.  
  
 `LocIsStatic`  
 Speicherort ist statisch.  
  
 `LocIsTLS`  
 Speicherort befindet sich im lokalen Threadspeicher.  
  
 `LocIsRegRel`  
 RELATIVE Register Speicherort befindet.  
  
 `LocIsThisRel`  
 Verwandter \- `this`Speicherort befindet.  
  
 `LocIsEnregistered`  
 Speicherort befindet sich in einem Register.  
  
 `LocIsBitField`  
 Speicherort befindet sich in einem Bitfeld.  
  
 `LocIsSlot`  
 Speicherort ist ein Slot MSIL \(Microsoft Intermediate Language\).  
  
 `LocIsIlRel`  
 MSIL\-RELATIVE Speicherort befindet.  
  
 `LocInMetaData`  
 Ort in den Metadaten.  
  
 `LocIsConstant`  
 Speicherort befindet sich in einem konstanten Wert.  
  
 `LocTypeMax`  
 Die Anzahl der Speicherort eintippungen diese Enumeration.  
  
## Hinweise  
 Die Eigenschaften, die für die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Schnittstelle verfügbar sind, hängt von der Position des Symbols in einer Bilddatei ab.  Weitere Informationen finden Sie unter [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Die Werte in dieser Enumeration werden von einem Aufruf der [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)