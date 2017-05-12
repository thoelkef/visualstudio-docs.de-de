---
title: "setUTCDate-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, Festlegen"
  - "Datumsangaben, UTC"
  - "setUTCDate-Methode"
  - "UTC-Datumsangaben, Festlegen"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate-Methode (Datum) (JavaScript)
Legt den numerischen Wert für den Tag des Monats in einem `Date`\-Objekt unter Verwendung der UTC \(Universal Time Coordinated, koordinierte Weltzeit\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 *numDate*  
 Erforderlich.  Ein dem Tag des Monats entsprechender numerischer Wert.  
  
## Hinweise  
 Zum Festlegen des Tags des Monats unter Verwendung der Ortszeit verwenden Sie die `setDate`\-Methode.  
  
 Wenn der *numDate*\-Wert größer als die Anzahl der Tage des im **Date**\-Objekt gespeicherten Monats oder eine negative Zahl ist, wird das Datum auf einen Wert gleich *numDate* minus der Anzahl der Tage des gespeicherten Monats festgelegt.  Wenn z. B. das gespeicherte Datum "05. Januar 1996" ist und **setUTCDate\(32\)** aufgerufen wird, wird das Datum in "01. Februar 1996" geändert.  Negative Zahlen haben eine ähnliche Auswirkung.  
  
 Mit der **setUTCFullYear**\-Methode können Jahr, Monat und Tag des Monats festgelegt werden.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCDate`\-Methode veranschaulicht.  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getDate\-Methode \(Datum\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate\-Methode \(Datum\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate\-Methode \(Datum\)](../../javascript/reference/setdate-method-date-javascript.md)