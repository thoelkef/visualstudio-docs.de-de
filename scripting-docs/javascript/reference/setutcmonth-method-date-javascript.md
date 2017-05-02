---
title: "setUTCMonth-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "Month-Methode"
  - "setUTCMonth-Methode"
  - "UTC-Datumsangaben, Festlegen"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth-Methode (Datum) (JavaScript)
Legt den Wert des Monats im `Date`\-Objekt unter Verwendung von UTC \(Universal Time Coordinated, koordinierte Weltzeit\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMonth`  
 Erforderlich.  Ein dem Monat entsprechender numerischer Wert.  Januar hat den Wert 0, und die nachfolgenden Werte geben die weiteren Monate an.  
  
 `dateVal`  
 Optional.  Ein numerischer Wert, der den Tag des Monats darstellt.  Ohne Angabe dieses Werts wird der Wert aus einem Aufruf der `getUTCDate`\-Methode verwendet.  
  
## Hinweise  
 Um den Monat unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setMonth`\-Methode.  
  
 Wenn der Wert von `numMonth` größer als 11 \(Januar entspricht dem Monat 0\) oder eine negative Zahl ist, wird der Wert für das gespeicherte Jahr entsprechend erhöht oder gesenkt.  Wenn das gespeicherte Datum z. B. "5. Jan 1996 00:00:00.00" lautet und **setUTCMonth\(14\)** aufgerufen wird, ändert sich das Datum in "5. März 1997 00:00:00.00".  
  
 Mit der **setUTCFullYear**\-Methode können Jahr, Monat und Tag des Monats festgelegt werden.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCMonth`\-Methode veranschaulicht.  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMonth\-Methode \(Datum\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth\-Methode \(Datum\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth\-Methode \(Datum\)](../../javascript/reference/setmonth-method-date-javascript.md)