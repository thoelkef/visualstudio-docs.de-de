---
title: "getMinutes-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes-Methode"
  - "minutes-Methode"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes-Methode (Datum) (JavaScript)
Ruft die Minuten eines `Date`\-Objekts unter Verwendung der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj.getMinutes()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück.  Es wird 0 \(null\) zurückgegeben, wenn die Zeit kleiner ist als eine Minute nach der Stunde.  Wenn ein `Date`\-Objekt erstellt wurde, ohne die Zeit anzugeben, ist der Minutenwert standardmäßig 0.  
  
## Hinweise  
 Um den Minutenwert unter Verwendung der koordinierten Weltzeit \(Universal Time Coordinated, UTC\) abzurufen, verwenden Sie die `getUTCMinutes`\-Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getMinutes`\-Methode veranschaulicht.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCMinutes\-Methode \(Datum\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes\-Methode \(Datum\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes\-Methode \(Datum\)](../../javascript/reference/setutcminutes-method-date-javascript.md)