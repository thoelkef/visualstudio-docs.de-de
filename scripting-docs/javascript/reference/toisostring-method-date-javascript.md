---
title: "toISOString-Methode (Datum) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toISOString-Methode [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString-Methode (Datum) (JavaScript)
Gibt ein Datum als Zeichenfolgenwert im ISO\-Format zurück.  
  
## Syntax  
  
```javascript  
  
objDate.toISOString()  
```  
  
## Rückgabewert  
 Eine Zeichenfolgendarstellung des Datums im ISO\-Format \(ISO \= International Organisation for Standardization, Internationale Organisation für Normung\).  
  
## Ausnahmen  
 Wenn `objDate` kein gültiges Datum enthält, wird eine `RangeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Das ISO\-Format ist eine Vereinfachung des Formats ISO 8601.  Weitere Informationen finden Sie unter [Datum\- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md).  
  
 Die Zeitzone ist immer UTC, angegeben durch das Suffix Z in der Ausgabe.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toISOString`\-Methode veranschaulicht.  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Date\-Objekt](../../javascript/reference/date-object-javascript.md)   
 [Datum\- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md)