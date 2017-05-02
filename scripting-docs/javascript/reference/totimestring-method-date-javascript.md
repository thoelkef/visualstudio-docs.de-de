---
title: "toTimeString-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString-Methode"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString-Methode (Datum) (JavaScript)
Gibt eine Uhrzeit als Zeichenfolgenwert zurück.  
  
## Syntax  
  
```  
  
objDate. toTimeString( )  
```  
  
## Hinweise  
 Der erforderliche `objDate`\-Verweis ist ein `Date`\-Objekt.  
  
 Die `toTimeString`\-Methode gibt einen Zeichenfolgenwert zurück, der die Uhrzeit in der aktuellen Zeitzone enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird die Zeit auf 2000 Millisekunden nach Mitternacht am 1. Januar 1970 UTC festgelegt und anschließend ausgeschrieben.  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
## Siehe auch  
 [toDateString\-Methode \(Datum\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString\-Methode \(Datum\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)