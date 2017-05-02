---
title: "setDate-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate-Methode"
  - "Datumsangaben, Festlegen"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate-Methode (Datum) (JavaScript)
Legt den numerischen Tag\-von\-dMONTH\-Wert des `Date`\-Objekts unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein `Date`\-Objekt.  
  
 `numDate`  
 Erforderlich.  Ein dem Tag des Monats entsprechender numerischer Wert.  
  
## Hinweise  
 Um den Tag\-von\-dMONTH\-Wert mithilfe der koordinierten Weltzeit \(UTC\) festzulegen, verwenden Sie die `setUTCDate`\-Methode.  
  
 Wenn der Wert von `numDate` größer als die Anzahl der Tage im Monat ist, erweitert das Datum nach zu einem späteren Monat und\/oder zu einem Jahr.  Wenn das gespeicherte Datum am 5. Januar 1996 ist und `setDate(32)` aufgerufen wird, ändert das Datum auf das 1. Februar 1996.  Wenn `numDate` eine negative Zahl ist, erweitert das Datum zurück zu einem früheren Monat und\/oder ein Jahr.  Wenn das gespeicherte Datum am 5. Januar 1996 ist und `setDate(-32)` aufgerufen wird, ändert das Datum auf das 29. November 1995.  
  
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md) kann verwendet werden, um das Jahr, den Monat und den Tag des Monats festzulegen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setDate`\-Methode gezeigt.  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getDate\-Methode \(Datum\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth\-Methode \(Datum\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate\-Methode \(Datum\)](../../javascript/reference/setutcdate-method-date-javascript.md)