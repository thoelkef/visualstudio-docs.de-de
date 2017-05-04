---
title: "setUTCMinutes-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "Minuten"
  - "setUTCMinutes-Methode"
  - "UTC-Zeiten, Festlegen"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes-Methode (Datum) (JavaScript)
Legt den Wert der Minuten im `Date`\-Objekt unter Verwendung der koordinierte Weltzeit \(UTC, Universal Coordinated Time\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMinutes`  
 Erforderlich.  Ein den Minuten entsprechender numerischer Wert.  Muss angegeben werden, wenn eines der beiden folgenden Argumente verwendet wird.  
  
 *numSeconds*  
 Optional.  Ein den Sekunden entsprechender numerischer Wert.  Muss angegeben werden, wenn `numMilli` verwendet wird.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das *numSeconds*\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] den Wert, der von der `getUTCSeconds`\-Methode zurückgegeben wird.  
  
 Um den Minutenwert unter Verwendung der Ortszeit zu ändern, verwenden Sie die `setMinutes`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00.00" ist und **setUTCMinutes\(70\)** aufgerufen wird, dann wird das Datum in "5. Jan 1996, 01:10:00.00" geändert.  
  
 Mit der **setUTCHours**\-Methode können Sie die Stunden, Minuten, Sekunden und Millisekunden festlegen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCMinutes`\-Methode veranschaulicht:  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMinutes\-Methode \(Datum\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes\-Methode \(Datum\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes\-Methode \(Datum\)](../../javascript/reference/setminutes-method-date-javascript.md)