---
title: "getUTCMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Millisekunden"
  - "UTC-Zeiten, zurückgeben"
  - "getUTCMilliseconds-Methode"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds-Methode (Datum) (JavaScript)
Ruft die Millisekunden `Date` eines Objekts unter Verwendung der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt einen\) zurück, der von 0\-999 reichen kann.  
  
## Hinweise  
 Um die Anzahl der Millisekunden in der Ortszeit abzurufen, verwenden Sie die `getMilliseconds`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCMilliseconds`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMilliseconds\-Methode \(Datum\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds\-Methode \(Datum\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds\-Methode \(Datum\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)