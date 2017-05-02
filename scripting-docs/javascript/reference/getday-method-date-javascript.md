---
title: "getDay-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay-Methode"
  - "Date-Objekt"
  - "Datumsangaben, Zurückgeben des Wochentags"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay-Methode (Datum) (JavaScript)
Ruft den Wochentag unter Verwendung der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj. getDay()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Ein Ganzzahlwert zwischen 0 und 6, der den Wochentag darstellt \(Sonntag ist 0, Samstag ist 6\).  
  
## Hinweise  
 Um den Wochentag unter Verwendung der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) zu bestimmen, verwenden Sie die `getUTCDay`\-Methode.  
  
 Im folgenden Beispiel wird die Verwendung der `getDay`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCDay\-Methode \(Datum\)](../../javascript/reference/getutcday-method-date-javascript.md)