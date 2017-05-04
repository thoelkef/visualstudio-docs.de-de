---
title: "setHours-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, Festlegen"
  - "Stunden"
  - "setHours-Methode"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setHours-Methode (Datum) (JavaScript)
Legt den Stundenwert im `Date`\-Objekt unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numHours`  
 Erforderlich.  Ein dem Stundenwert entsprechender numerischer Wert.  
  
 `numMin`  
 Optional.  Ein den Minuten entsprechender numerischer Wert.  Muss angegeben werden, wenn eines der beiden folgenden Argumente verwendet wird.  
  
 `numSec`  
 Optional.  Ein den Sekunden entsprechender numerischer Wert.  Muss angegeben werden, wenn das folgende Argument verwendet wird.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das `numMinutes`\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] den Wert, der von der `getMinutes`\-Methode zurückgegeben wird.  
  
 Um den Stundenwert unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) festzulegen, verwenden Sie die `setUTCHours`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00" ist und **setHours\(30\)** aufgerufen wird, ändert sich das Datum in "6. Jan 1996, 06:00:00". Negative Zahlen haben eine ähnliche Auswirkung.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setHours`\-Methode veranschaulicht.  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getHours\-Methode \(Datum\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours\-Methode \(Datum\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours\-Methode \(Datum\)](../../javascript/reference/setutchours-method-date-javascript.md)