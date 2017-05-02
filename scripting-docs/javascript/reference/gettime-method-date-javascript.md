---
title: "getTime-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime-Methode"
  - "time-Methode"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime-Methode (Datum) (JavaScript)
Ruft den Zeitwert in Millisekunden ab.  
  
## Syntax  
  
```  
  
dateObj.getTime()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt die Anzahl von Millisekunden zurück, die zwischen dem 1. Januar 1970, Mitternacht, und dem im `Date`\-Objekt enthaltenen Uhrzeitwert verstrichen sind.  Der Datumsbereich beträgt ungefähr 285.616 Jahre vor und nach Mitternacht des 1. Januar 1970.  Negative Zahlen geben Datumswerte vor 1970 an.  
  
## Hinweise  
 Bei umfangreichen Datums\- und Zeitkalkulationen ist es häufig sinnvoll, Variablen zu definieren, die der Anzahl von Millisekunden eines Tages, einer Stunde oder einer Minute entsprechen.  Beispiel:  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Weitere Informationen zur Verwendung der `getTime`\-Methode finden Sie unter [Berechnen von Datum und Uhrzeit \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getTime`\-Methode veranschaulicht.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [setTime\-Methode \(Datum\)](../../javascript/reference/settime-method-date-javascript.md)