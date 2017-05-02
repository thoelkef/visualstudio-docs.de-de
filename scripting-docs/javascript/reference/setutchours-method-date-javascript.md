---
title: "setUTCHours-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "setUTCHours-Methode"
  - "UTC-Zeiten, Festlegen"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setUTCHours-Methode (Datum) (JavaScript)
Legt unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC \) den Stundenwert im `Date`\-Objekt fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numHours`  
 Erforderlich.  Ein dem Stundenwert entsprechender numerischer Wert.  
  
 `numMin`  
 Optional.  Ein den Minuten entsprechender numerischer Wert.  Muss angegeben werden, wenn `numSec` oder `numMilli` verwendet werden.  
  
 `numSec`  
 Optional.  Ein den Sekunden entsprechender numerischer Wert.  Muss angegeben werden, wenn das `numMilli`\-Argument verwendet wird.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das `numMin`\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] den Wert, der von der `getUTCMinutes`\-Methode zurückgegeben wird.  
  
 Um den Stundenwert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setHours`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00.00" ist und **setUTCHours\(30\)** aufgerufen wird, dann wird das Datum in "6. Jan 1996, 06:00:00.00" geändert.  
  
## Beispiel  
 Im folgenden Beispiel wird die `setUTCHours`\-Methode veranschaulicht.  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getHours\-Methode \(Datum\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours\-Methode \(Datum\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours\-Methode \(Datum\)](../../javascript/reference/sethours-method-date-javascript.md)