---
title: "setSeconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds-Methode"
  - "setSeconds-Methode"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds-Methode (Datum) (JavaScript)
Legt den Sekundenwert im `Date`\-Objekt unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 *numSeconds*  
 Erforderlich.  Ein den Sekunden entsprechender numerischer Wert.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das `numMilli`\-Argument nicht angegeben wird, wird in [!INCLUDE[javascript](../../includes/javascript-md.md)] der von der **getMilliseconds**\-Methode zurückgegebene Wert verwendet wird.  
  
 Um den Sekundenwert unter Verwendung der koordinierten Weltzeit \(Universal Time Coordinated, UTC\) festzulegen, verwenden Sie die `setUTCSeconds`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00" ist und **setSeconds\(150\)** aufgerufen wird, dann wird das Datum in "5. Jan 1996, 00:02:30" geändert.  
  
 Mit der `setHours`\-Methode können Sie die Stunden, Minuten, Sekunden und Millisekunden festlegen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setSeconds`\-Methode veranschaulicht.  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getSeconds\-Methode \(Datum\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds\-Methode \(Datum\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds\-Methode \(Datum\)](../../javascript/reference/setutcseconds-method-date-javascript.md)