---
title: "CV_access_e | Microsoft Docs"
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
  - "CV_access_e-Enumeration"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Bereich der Sichtbarkeit \(Zugriffsebene\) von Memberfunktionen und Variablen an.  
  
## Syntax  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elements  
 CV\_private  
 Private Member zugreifen.  
  
 CV\_protected  
 Member hat Zugriff geschützt.  
  
 CV\_public  
 öffentlichen Member besitzt Zugriff.  
  
## Hinweise  
 Der `friend` Zugriffsspezifizierer wird hier nicht eingeschlossen, da sie in der Regel durch Nichtmitglieds Funktionen verwendet wird, die Zugriff auf private und geschützte übergeordneten Klasse haben.  Verwenden Sie die [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)\-Methode, um Symbole mit `SymTagFriend` Zugriff gesucht werden soll.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)