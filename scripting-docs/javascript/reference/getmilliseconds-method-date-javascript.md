---
title: "getMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Millisekunden"
  - "getMilliseconds-Methode"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds-Methode (Datum) (JavaScript)
Ruft die Millisekunden eines Datumswerts ab, unter Verwendung der lokalen Zeit.  
  
## Syntax  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Ruft die Millisekunden eines Datumswerts ab  Der Wert kann im Bereich 0 bis 999 liegen.  Wenn ein Datum ohne Angabe der Millisekunden erstellt wurde, wird der Wert 0 \(null\) zurückgegeben.  
  
## Hinweise  
 Um die Anzahl der Millisekunden unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) zu bestimmen, verwenden Sie die `getUTCMilliseconds`\-Methode.  
  
## Beispiel  
 Das folgende Beispiel zeigt die Anwendung der **getMilliseconds**\-Methode.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds\-Methode \(Datum\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)