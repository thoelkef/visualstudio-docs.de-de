---
title: "getUTCMinutes-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Minuten"
  - "UTC-Zeiten, zurückgeben"
  - "getUTCMinutes-Methode"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes-Methode (Datum) (JavaScript)
Ruft die Minuten `Date` eines Objekts unter Verwendung der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück.  Null wird die Zeit ist kleiner als eine Minute nach der Stunde zurückgegeben.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Uhrzeit anzugeben, ist standardmäßig der UTC\-Minutenwert 0.  In anderen Zeitzonen kann er unterschiedlich.  
  
## Hinweise  
 Um die gespeicherte Anzahl der Minuten unter Verwendung der Ortszeit abzurufen, verwenden Sie die `getMinutes`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCMinutes`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMinutes\-Methode \(Datum\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes\-Methode \(Datum\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes\-Methode \(Datum\)](../../javascript/reference/setutcminutes-method-date-javascript.md)