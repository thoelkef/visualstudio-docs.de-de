---
title: "getUTCDay-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date-Objekt"
  - "Datumsangaben, UTC"
  - "UTC-Datumsangaben, Zurückgeben"
  - "getUTCDay-Methode"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay-Methode (Datum) (JavaScript)
Ruft den Wochentag mithilfe der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 \(Sonntag\) und 6 \(Samstag\) zurück, die den Wochentag darstellt.  
  
## Hinweise  
 Um den Wochentag unter Verwendung der Ortszeit zu bestimmen, verwenden Sie die `getDate`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCDay`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getDay\-Methode \(Datum\)](../../javascript/reference/getday-method-date-javascript.md)