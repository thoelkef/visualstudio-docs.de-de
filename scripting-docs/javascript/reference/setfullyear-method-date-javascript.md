---
title: "setFullYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year-Methode"
  - "setFullYear-Methode"
  - "Datumsangaben, festlegen"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear-Methode (Datum) (JavaScript)
Legt das Jahr des `Date`\-Objekts unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein `Date`\-Objekt.  
  
 `numYear`  
 Erforderlich.  Ein numerischer Wert während des Jahrs.  
  
 `numMonth`  
 Dies ist optional.  Ein nullbasierter numerischer Wert für den Monat \(0 für Januar, 11 für Dezember\).  Muss angegeben werden, wenn `numDate` angegeben wird.  
  
 `numDate`  
 Dies ist optional.  Ein numerischer Wert gleich während Tag des Monats.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn das optionale Argument nicht angegeben wurde.  Wenn das `numMonth`\-Argument optional ist, jedoch kein angegeben, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet, die der Wert von der **getMonth**\-Methode zurückgegeben wurde.  
  
 Wenn der Wert eines Arguments größer als sein Kalenderbereich ist oder negativ ist, die Datumsrollforwards oder das rückwärts nach Bedarf.  
  
 Um das Jahr koordinierte Weltzeit \(UTC\) bei festzulegen, verwenden Sie die `setUTCFullYear`\-Methode.  
  
 Der Bereich von den Jahren, die in das Date\-Objekt unterstützt werden, ist ungefähr 285.616 Jahre vor und nach 1970.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `setFullYear`\-Methode:  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getFullYear\-Methode \(Datum\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear\-Methode \(Datum\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear\-Methode \(Datum\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)