---
title: "setMonth-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month-Methode"
  - "setMonth-Methode"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth-Methode (Datum) (JavaScript)
Legt den Wert des Monats im `Date`\-Objekt unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMonth`  
 Erforderlich.  Ein dem Monat entsprechender numerischer Wert.  Januar hat den Wert 0, und die nachfolgenden Werte geben die weiteren Monate an.  
  
 `dateVal`  
 Optional.  Ein numerischer Wert, der den Tag des Monats darstellt.  Ohne Angabe dieses Werts wird der Wert aus einem Aufruf der `getDate`\-Methode verwendet.  
  
## Hinweise  
 Um den Monatswert unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) festzulegen, verwenden Sie die `setUTCMonth`\-Methode.  
  
 Ist der Wert von `numMonth` größer als 11 \(Januar entspricht dem Monat 0\) oder eine negative Zahl, wird das gespeicherte Jahr entsprechend geändert.  Wenn das gespeicherte Datum z. B. "5. Jan 1996" lautet und **setMonth\(14\)** aufgerufen wird, ändert sich das Datum in "5. März 1997".  
  
 Mit der **setFullYear**\-Methode können Jahr, Monat und Tag des Monats festgelegt werden.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMonth`\-Methode veranschaulicht.  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMonth\-Methode \(Datum\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth\-Methode \(Datum\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth\-Methode \(Datum\)](../../javascript/reference/setutcmonth-method-date-javascript.md)