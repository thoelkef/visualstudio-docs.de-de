---
title: "setMinutes-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Minuten"
  - "setMinutes-Methode"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes-Methode (Datum) (JavaScript)
Legt den Wert der Minuten im **Date**\-Objekt unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMinutes`  
 Erforderlich.  Ein den Minuten entsprechender numerischer Wert.  Muss angegeben werden, wenn eines der beiden folgenden Argumente verwendet wird.  
  
 *numSeconds*  
 Optional.  Ein den Sekunden entsprechender numerischer Wert.  Muss angegeben werden, wenn das `numMilli`\-Argument verwendet wird.  
  
 `numMilli`  
 Optional.  Ein den Millisekunden entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das *numSeconds*\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../includes/javascript-md.md)] den Wert, der von der `getSeconds`\-Methode zurückgegeben wird.  
  
 Um den Minutenwert unter Verwendung der koordinierten Weltzeit \(Universal Time Coordinated, UTC\) festzulegen, verwenden Sie die `setUTCMinutes`\-Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert.  Wenn z. B. das gespeicherte Datum "5. Jan 1996, 00:00:00" ist und **setMinutes\(90\)** aufgerufen wird, dann wird das Datum in "5. Jan 1996, 01:30:00" geändert. Negative Zahlen haben eine ähnliche Auswirkung.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMinutes`\-Methode veranschaulicht.  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMinutes\-Methode \(Datum\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes\-Methode \(Datum\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes\-Methode \(Datum\)](../../javascript/reference/setutcminutes-method-date-javascript.md)