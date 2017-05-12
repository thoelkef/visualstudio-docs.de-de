---
title: "getUTCFullYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear-Methode"
  - "Date-Objekt"
  - "UTCFullYear-Methode"
  - "Datumsangaben, UTC"
  - "UTC-Datumsangaben, Zurückgeben"
  - "Full Year-Methode"
  - "UTC-Datumsangaben, Abrufen"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear-Methode (Datum) (JavaScript)
Ruft das Jahr unter Verwendung der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt das Jahr als vierstellige Zahl zurück.  Bei Jahren, die mit zwei Ziffern im `Date`\-Konstruktor oder in `setFullYear` angegeben werden, wird davon ausgegangen, dass sie im zwanzigsten Jahrhundert liegen. Somit gibt `getUTCFullYear` für "5\/14\/12" den Wert "1912" zurück.  
  
## Hinweise  
 Um das Jahr unter Verwendung der Ortszeit abzurufen, verwenden Sie die `getFullYear`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCFullYear`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getFullYear\-Methode \(Datum\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear\-Methode \(Datum\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)