---
title: "Date.now-Funktion (JavaScript) | Microsoft Docs"
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
  - "now-Methode"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Date.now-Funktion (JavaScript)
Ruft das aktuelle Datum und die aktuelle Uhrzeit ab.  
  
## Syntax  
  
```  
  
Date.now()  
```  
  
## Rückgabewert  
 Die Anzahl der Millisekunden zwischen dem 1. Januar 1970 um 0:00 Uhr und dem aktuellen Datum und der Uhrzeit.  
  
## Hinweise  
 Die [getTime\-Methode](../../javascript/reference/gettime-method-date-javascript.md) gibt die Anzahl der Millisekunden zwischen dem 1. Januar 1970 und einem angegebenen Datum zurück.  
  
 Informationen darüber, wie verstrichene Zeit berechnet und Datumsangaben verglichen werden, finden Sie unter [Berechnen von Datum und Uhrzeit \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `now`\-Methode veranschaulicht.  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## Anforderungen  
 Wird nicht in installierten Versionen unterstützt, die älter sind als Internet Explorer 9.  Wird jedoch in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6 \(Standardmodus\), Internet Explorer 7 \(Standardmodus\), Internet Explorer 8 \(Standardmodus\), Internet Explorer 9 \(Standardmodus\) und Internet Explorer 10 \(Standardmodus\).  Wird außerdem in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps unterstützt.  
  
## Siehe auch  
 [getTime\-Methode \(Datum\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date\-Objekt](../../javascript/reference/date-object-javascript.md)   
 [Berechnen von Datum und Uhrzeit \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript\-Methoden](../../javascript/reference/javascript-methods.md)