---
title: "Date.parse-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse-Funktion [JavaScript]"
  - "parse-Funktion [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse-Funktion (JavaScript)
Analysiert eine Zeichenfolge mit einem Datum und gibt die Anzahl der Millisekunden zwischen diesem Datum und Mitternacht des 1. Januars 1970 zurück.  
  
## Syntax  
  
```  
Date.parse(dateVal)   
```  
  
## Hinweise  
 Das erforderliche `dateVal`\-Argument ist entweder eine Zeichenfolge, die ein Datum enthält, oder ein Wert, der aus einem ActiveX\-Objekt oder einem anderen Objekt abgerufen wird.  Informationen über Datumszeichenfolgen, die die `Date.parse`\-Funktion analysieren kann, finden Sie unter [Datum\- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md).  
  
 Die `Date.parse`\-Funktion gibt einen ganzzahligen Wert zurück, der der Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970 und dem in `dateVal` angegebenen Datum entspricht.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Date.parse`\-Funktion.  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Differenz zwischen dem angegebenen Datum und dem 1.1.1970 zurückgegeben.  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [getDate\-Methode \(Datum\)](../../javascript/reference/getdate-method-date-javascript.md)