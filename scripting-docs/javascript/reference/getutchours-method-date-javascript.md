---
title: "getUTCHours-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Stunden"
  - "UTC-Zeiten, zurückgeben"
  - "getUTCHours-Methode"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours-Methode (Datum) (JavaScript)
Ruft den Wert der Stunden in einem `Date`\-Objekt mithilfe der koordinierten Weltzeit \(UTC\) ab.  
  
## Syntax  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 23 die Anzahl von Stunden ab Mitternacht angibt zurück.  Null wird zurückgegeben, wenn die Zeit vor 1:00 ist: 00 Uhr.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Uhrzeit anzugeben, befindet sich die Stunde 0 in der UTC\-Zeit.  Dieses Mal ist auch in anderen Zeitzonen ungleich 0 \(null\).  
  
## Hinweise  
 Um die Anzahl der seit Mitternacht vergangenen Stunden unter Verwendung der Ortszeit zu bestimmen, verwenden Sie die `getHours`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCHours`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getHours\-Methode \(Datum\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours\-Methode \(Datum\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours\-Methode \(Datum\)](../../javascript/reference/setutchours-method-date-javascript.md)