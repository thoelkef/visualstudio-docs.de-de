---
title: "DataKind | Microsoft Docs"
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
  - "DataKind-Enumeration"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den bestimmten Bereich eines Datenwerts an.  
  
## Syntax  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elements  
 DataIsUnknown  
 Symbol für Daten kann nicht bestimmt werden.  
  
 DataIsLocal  
 Datenelement ist eine lokale Variable.  
  
 DataIsStaticLocal  
 Datenelement ist eine statische lokale Variable.  
  
 DataIsParam  
 Datenelement ist ein formaler Parameter.  
  
 DataIsObjectPtr  
 Datenelement ist ein Objektzeiger \(`this`\).  
  
 DataIsFileStatic  
 Datenelement ist eine FILE\-bewertete Variablen.  
  
 DataIsGlobal  
 Datenelement ist eine globale Variable.  
  
 DataIsMember  
 Datenelement ist ein Objekt membervariable.  
  
 DataIsStaticMember  
 Datenelement ist eine Klassen statische Variable.  
  
 DataIsConstant  
 Datenelement ist ein konstanter Wert.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von der [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)