---
title: "UdtKind | Microsoft Docs"
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
  - "UdtKind-Enumeration"
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UdtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Beschreibt die Vielzahl von benutzerdefinierten Typ \(UDT\).  
  
## Syntax  
  
```cpp#  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## Elements  
 UdtStruct  
 UDT ist eine Struktur.  
  
 UdtClass  
 UDT ist eine Klasse.  
  
 UdtUnion  
 UDT ist eine Union.  
  
 UdtInterface  
 UDT ist eine Schnittstelle.  
  
## Hinweise  
 Die Werte in dieser Enumeration zurückgegeben von der [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) Methode.  
  
## Anforderungen  
 Header: dia2.idl  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)