---
title: "setMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Millisekunden"
  - "setMilliseconds-Methode"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds-Methode (Datum) (JavaScript)
Legt den Millisekundenwert im `Date`\-Objekt unter Verwendung der Ortszeit fest.  
  
## Syntax  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMilli`  
 Erforderlich.  Ein dem Millisekundenwert entsprechender numerischer Wert.  
  
## Hinweise  
 Um den Millisekundenwert unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) festzulegen, verwenden Sie die `setUTCMilliseconds`\-Methode.  
  
 Wenn der Wert von `numMilli` größer als 999 oder eine negative Zahl ist, wird die gespeicherte Anzahl der Sekunden \(und, falls erforderlich, der Minuten, Stunden usw.\) um eine entsprechende Anzahl erhöht.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMilliseconds`\-Methode veranschaulicht.  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMilliseconds\-Methode \(Datum\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)