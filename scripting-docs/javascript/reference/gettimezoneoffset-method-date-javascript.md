---
title: "getTimezoneOffset-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset-Methode"
  - "Zeitzonen [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset-Methode (Datum) (JavaScript)
Ruft die Differenz zwischen der Zeit auf dem lokalem Computer und der UTC \(Universal Coordinated Time, koordinierte Weltzeit\) in Minuten ab.  
  
## Syntax  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### Parameter  
 Der erforderliche `dateObj`\-Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt die Anzahl von Minuten zwischen der Zeit auf dem aktuellen Computer \(entweder der Clientcomputer oder, wenn diese Methode von einem Serverskripts aufgerufen wird, der Server\) und der UTC zurück.  Es ist positiv, wenn die aktuelle lokale Zeit des Computers hinter der UTC liegt \(z. B. pazifische Sommerzeit\), und negativ, wenn die aktuelle lokale Zeit des Computers vor der UTC liegt \(z. B. Japan\).  Wenn ein Server in New York City von einem Client in Los Angeles am 1. Dezember abgefragt wird, gibt `getTimezoneOffset` 480 zurück, wenn dieser Aufruf auf dem Client ausgeführt wird, und 300, wenn er auf dem Server ausgeführt wird.  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getTimezoneOffset`\-Methode veranschaulicht.  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getTime\-Methode \(Datum\)](../../javascript/reference/gettime-method-date-javascript.md)