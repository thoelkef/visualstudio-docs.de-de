---
title: "getFullYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, Zurückgeben des Jahres"
  - "Date-Objekt"
  - "getFullYear-Methode"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear-Methode (Datum) (JavaScript)
Ruft das Jahr anhand der Ortszeit ab.  
  
## Syntax  
  
```  
  
dateObj.getFullYear()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Das Jahr als vierstellige Zahl.  Beispielsweise wird das Jahr 1976 als "1976" zurückgegeben.  Bei Jahren, die mit zwei Ziffern im `Date`\-Konstruktor oder in `setFullYear` angegeben werden, wird davon ausgegangen, dass sie im zwanzigsten Jahrhundert liegen. Somit gibt `getFullYear` für "5\/14\/12" den Wert "1912" zurück.  
  
## Hinweise  
 Um das Jahr mithilfe der koordinierten Weltzeit \(Universal Coordinated Time, UTC\) zu bestimmen, verwenden Sie die `getUTCFullYear`\-Methode.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **getFullYear**\-Methode.  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getUTCFullYear\-Methode \(Datum\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear\-Methode \(Datum\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)