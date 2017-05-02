---
title: "getUTCDate-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date-Objekt"
  - "Datumsangaben, UTC"
  - "UTC-Datumsangaben, Zurückgeben"
  - "getUTCDate-Methode"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate-Methode (Datum) (JavaScript)
Ruft den Monatstag mithilfe der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 1 und 31 zurück, die den Monatstag darstellt.  
  
## Hinweise  
 Zum Abrufen des Tags des Monats unter Verwendung der Ortszeit verwenden Sie die `getDate`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCDate`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getDate\-Methode \(Datum\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate\-Methode \(Datum\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate\-Methode \(Datum\)](../../javascript/reference/setutcdate-method-date-javascript.md)