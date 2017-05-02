---
title: "getUTCSeconds-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC-Zeiten, zurückgeben"
  - "seconds-Methode"
  - "getUTCSeconds-Methode"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds-Methode (Datum) (JavaScript)
Ruft die Sekunden eines `Date`\-Objekts unter Verwendung der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück.  Null wird zurückgegeben, wenn die Zeit kleiner als eine Sekunde in die aktuelle Minute ist.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Uhrzeit anzugeben, ist standardmäßig der UTC\-Sekundenwert 0.  
  
## Hinweise  
 Um die Anzahl der Sekunden unter Verwendung der Ortszeit zu bestimmen, verwenden Sie die `getSeconds`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCSeconds`\-Methode gezeigt.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getSeconds\-Methode \(Datum\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds\-Methode \(Datum\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds\-Methode \(Datum\)](../../javascript/reference/setutcseconds-method-date-javascript.md)