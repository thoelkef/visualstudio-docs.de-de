---
title: "getUTCMonth-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "UTC-Datumsangaben, Zurückgeben"
  - "Month-Methode"
  - "getUTCMonth-Methode"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth-Methode (Datum) (JavaScript)
Ruft den Monat eines `Date`\-Objekts unter Verwendung der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 \(Januar\) und 11 zurück \(Dezember\).  
  
## Hinweise  
 Um den Monat unter Verwendung der Ortszeit zu bestimmen, verwenden Sie die **getMonth**\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCMonth`\-Methode gezeigt.  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getMonth\-Methode \(Datum\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth\-Methode \(Datum\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth\-Methode \(Datum\)](../../javascript/reference/setutcmonth-method-date-javascript.md)