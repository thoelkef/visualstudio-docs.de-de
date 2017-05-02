---
title: "setUTCMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "Millisekunden"
  - "setUTCMilliseconds-Methode"
  - "UTC-Zeiten, Festlegen"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds-Methode (Datum) (JavaScript)
Legt den Wert der Millisekunden im `Date`\-Objekt unter Verwendung von UTC \(Universal Time Coordinated, koordinierte Weltzeit\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numMilli`  
 Erforderlich.  Ein dem Millisekundenwert entsprechender numerischer Wert.  
  
## Hinweise  
 Um den Millisekundenwert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setMilliseconds`\-Methode.  
  
 Wenn der Wert von `numMilli` größer als 999 oder eine negative Zahl ist, wird die gespeicherte Anzahl der Sekunden \(und, falls erforderlich, der Minuten, Stunden usw.\) um eine entsprechende Anzahl erhöht.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCMilliseconds`\-Methode veranschaulicht.  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMilliseconds\-Methode \(Datum\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds\-Methode \(Datum\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)