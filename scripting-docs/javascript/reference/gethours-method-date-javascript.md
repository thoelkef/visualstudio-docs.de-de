---
title: "getHours-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date-Objekt"
  - "GetHours-Methode"
  - "Hours-Methode"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours-Methode (Datum) (JavaScript)
Ruft die Stunden in einem Datum ab, unter Verwendung der Ortszeit.  
  
## Syntax  
  
```  
  
dateObj.getHours()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Ein Ganzzahlwert zwischen 0 und 23, welcher die Anzahl von seit Mitternacht vergangenen Stunden anzeigt.  Null \(0\) wird zurückgegeben, wenn die Zeit vor 1:00:00 liegt.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Zeit anzugeben, ist die Stunde standardmäßig 0.  
  
## Hinweise  
 Um den Stundenwert unter Verwendung der koordinierten Weltzeit \(Universal Time Coordinated, UTC\) abzurufen, verwenden Sie die `getUTCHours`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getHours`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCHours\-Methode \(Datum\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours\-Methode \(Datum\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours\-Methode \(Datum\)](../../javascript/reference/setutchours-method-date-javascript.md)