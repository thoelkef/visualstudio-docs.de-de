---
title: "getDate-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date-Objekt"
  - "Datumsangaben, zurückgegebener Tag des Monats"
  - "getDate-Methode"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate-Methode (Datum) (JavaScript)
Ruft den Monatstag unter Verwendung der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj.getDate()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Eine ganze Zahl zwischen 1 und 31, die den Monatstag darstellt.  
  
## Hinweise  
 Um den Monatstag unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) abzurufen, verwenden Sie die `getUTCDate`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getDate`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCDate\-Methode \(Datum\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate\-Methode \(Datum\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate\-Methode \(Datum\)](../../javascript/reference/setutcdate-method-date-javascript.md)