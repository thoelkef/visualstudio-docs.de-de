---
title: "Date.UTC-Funktion (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC-Funktion [JavaScript]"
  - "UTC-Datumsangaben, Zurückgeben"
  - "Date.UTC-Funktion [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC-Funktion (JavaScript)
Gibt die Anzahl von Millisekunden zwischen Mitternacht des 1. Januar 1970 UTC \(Universal Coordinated Time, koordinierte Weltzeit\) bzw. GMT und dem angegebenen Datum zurück.  
  
## Syntax  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Parameter  
 `year`  
 Erforderlich.  Die vollständige Jahresangabe ist für die Genauigkeit bei jahrhundertübergreifenden Datumsangaben erforderlich.  Wird für `year` ein Wert zwischen 0 und 99 verwendet, wird `year` als 1900 \+ `year` interpretiert.  
  
 `month`  
 Erforderlich.  Der Monat als ganze Zahl zwischen 0 und 11 \(Januar bis Dezember\).  
  
 `day`  
 Erforderlich.  Das Datum als ganze Zahl zwischen 1 und 31.  
  
 `hours`  
 Optional.  Muss angegeben werden, wenn `minutes` angegeben wird.  Eine ganze Zahl zwischen 0 und 23 \(Mitternacht bis 23 Uhr\), die die Stunde angibt.  
  
 `minutes`  
 Optional.  Muss angegeben werden, wenn `seconds` angegeben wird.  Eine ganze Zahl zwischen 0 und 59, die die Minuten angibt.  
  
 `seconds`  
 Optional.  Muss angegeben werden, wenn `milliseconds` angegeben wird.  Eine ganze Zahl zwischen 0 und 59, die die Sekunden angibt.  
  
 `ms`  
 Optional.  Eine ganze Zahl zwischen 0 und 999, die die Millisekunden angibt.  
  
## Hinweise  
 Die `Date.UTC`\-Funktion gibt die Anzahl der Millisekunden zwischen dem 1. Januar 1970, Mitternacht, und dem angegebenen Datum gemäß koordinierter Weltzeit \(Universal Coordinated Time, UTC\) zurück.  Dieser Rückgabewert kann in der `setTime`\-Methode und im `Date`\-Objektkonstruktor verwendet werden.  Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn Sie z. B. 150 Sekunden angeben, macht [!INCLUDE[javascript](../../includes/javascript-md.md)] daraus 2 Minuten und 30 Sekunden.  
  
 Der Unterschied zwischen der `Date.UTC`\-Funktion und dem `Date`\-Objektkonstruktor, der ein Datum akzeptiert, liegt darin, dass die `Date.UTC`\-Funktion von UTC und der `Date`\-Objektkonstruktor von der Ortszeit ausgeht.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Date.UTC`\-Funktion.  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [setTime\-Methode \(Datum\)](../../javascript/reference/settime-method-date-javascript.md)