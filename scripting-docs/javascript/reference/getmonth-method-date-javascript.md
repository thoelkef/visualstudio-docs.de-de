---
title: "getMonth-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date-Objekt"
  - "Datumsangaben, month-Wert"
  - "Month-Methode"
  - "GetMonth-Methode"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth-Methode (Datum) (JavaScript)
Ruft den Monat anhand der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj.getMonth()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Die `getMonth`\-Methode gibt einen Ganzzahlwert zwischen 0 \(Januar\) und 11 \(Dezember\) zurück.  Für ein mit "5. Januar 1996" definiertes `Date` gibt `getMonth` 0 zurück.  
  
## Hinweise  
 Um den Monatswert unter Verwendung der koordinierten Weltzeit \(Universal Time Coordinated, UTC\) abzurufen, verwenden Sie die `getUTCMonth`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getMonth`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCMonth\-Methode \(Datum\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth\-Methode \(Datum\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth\-Methode \(Datum\)](../../javascript/reference/setutcmonth-method-date-javascript.md)