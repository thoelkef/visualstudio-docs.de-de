---
title: "BasicType | Microsoft Docs"
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
  - "BasicType-Enumeration"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den einfachen Typ des Symbols an.  
  
## Syntax  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elements  
 btNoType  
 Kein einfachen Typ wird angegeben.  
  
 btVoid  
 Einfacher Typ ist `void`.  
  
 btChar  
 Einfacher Typ ist `char` \(C\/C\+\+\-Typ\).  
  
 btWChar  
 Einfacher Typ ist viele Zeichen \(Unicode\) \(`WCHAR`\).  
  
 btInt  
 Einfacher Typ ist `signed int` \(C\/C\+\+\-Typ\).  
  
 btUInt  
 Einfacher Typ ist `unsigned int` \(C\/C\+\+\-Typ\).  
  
 btFloat  
 Einfacher Typ ist eine Gleitkommazahl \(`FLOAT`\).  
  
 btBCD  
 Einfacher Typ ist eine verschlüsselte binär \(dezimal\)`BCD`.  
  
 btBool  
 Einfacher Typ ist ein boolescher Wert \(`BOOL`\).  
  
 btLong  
 Einfacher Typ ist `long int` \(C\/C\+\+\-Typ\).  
  
 btULong  
 Einfacher Typ ist `unsigned long int` \(C\/C\+\+\-Typ\).  
  
 btCurrency  
 Einfacher Typ ist Währung.  
  
 btDate  
 Einfacher Typ ist Datum\/Uhrzeit \(`DATE`\).  
  
 btVariant  
 Einfacher Typ ist eine Variablentyp Struktur \(`VARIANT`\).  
  
 btComplex  
 Einfacher Typ ist eine komplexe Zahl.  
  
 btBit  
 Einfacher Typ ist geringfügig.  
  
 btBSTR  
 Einfacher Typ ist eine grundlegende oder binäre Zeichenfolge \(`BSTR`\).  
  
 btHresult  
 Einfacher Typ ist `HRESULT`.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von der [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)