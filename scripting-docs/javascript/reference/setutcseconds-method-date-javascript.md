---
title: "setUTCSeconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "seconds-Methode"
  - "setUTCSeconds-Methode"
  - "UTC-Zeiten, Festlegen"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCSeconds-Methode (Datum) (JavaScript)
Legt den Wert der Sekunden im `Date`\-Objekt unter Verwendung von UTC \(Universal Time Coordinated, koordinierte Weltzeit\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 *numSeconds*  
 Erforderlich.  Ein den Sekunden entsprechender numerischer Wert.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das `numMilli`\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] den Wert, der von der `getUTCMilliseconds`\-Methode zurückgegeben wird.  
  
 Um den Sekundenwert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setSeconds`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00.00" ist und **setSeconds\(150\)** aufgerufen wird, dann wird das Datum in "5. Jan 1996, 00:02:30.00" geändert.  
  
 Mit der **setUTCHours**\-Methode können Sie die Stunden, Minuten, Sekunden und Millisekunden festlegen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCSeconds`\-Methode veranschaulicht.  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getSeconds\-Methode \(Datum\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds\-Methode \(Datum\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds\-Methode \(Datum\)](../../javascript/reference/setseconds-method-date-javascript.md)