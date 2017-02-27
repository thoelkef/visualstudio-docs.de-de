---
title: "NameSearchOptions | Microsoft Docs"
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
  - "NameSearchOptions-Enumeration"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Suchoptionen für Symbol und Dateinamen an.  
  
## Syntax  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Elements  
 `nsNone`  
 Es wurden keine Optionen angegeben.  
  
 `nsfCaseSensitive`  
 Wendet eine Übereinstimmung des Namens unter Berücksichtigung von Groß\- und Kleinschreibung.  
  
 `nsfCaseInsensitive`  
 Wendet eine Übereinstimmung Name der Groß\- und Kleinschreibung.  
  
 `nsfFNameExt`  
 Behandelt Namen als Pfade und wendet eine Übereinstimmung filename.ext\-Name.  
  
 `nsfRegularExpression`  
 Wendet eine Übereinstimmung des Namens unter Berücksichtigung von Groß\- und Kleinschreibung unter Verwendung von Sternchen \(\*\) und Fragezeichen \(?\) als Platzhalter.  
  
 `nsfUndecoratedName`  
 Gilt nur für Symbole, die ergänzten Namen und die Ergänzung rückgängig gemacht haben.  
  
## Hinweise  
 Die Werte dieser Enumeration werden mit den folgenden Methoden übergeben:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Anforderungen  
 Header: dia2.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)