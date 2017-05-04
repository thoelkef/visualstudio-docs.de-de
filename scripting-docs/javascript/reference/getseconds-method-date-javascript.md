---
title: "getSeconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds-Methode"
  - "GetSeconds-Methode"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds-Methode (Datum) (JavaScript)
Ruft die Sekunden eines Objekts, `Date` unter Verwendung der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj.getSeconds()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück.  Null wird zurückgegeben, wenn die Zeit kleiner als eine Sekunde in die aktuelle Minute ist.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Uhrzeit anzugeben, ist standardmäßig der Sekundenwert 0.  
  
## Hinweise  
 Um den Sekundenwert mithilfe der koordinierten Weltzeit \(UTC\) abzurufen, verwenden Sie die `getUTCSeconds`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getSeconds`\-Methode gezeigt.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCSeconds\-Methode \(Datum\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds\-Methode \(Datum\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds\-Methode \(Datum\)](../../javascript/reference/setutcseconds-method-date-javascript.md)