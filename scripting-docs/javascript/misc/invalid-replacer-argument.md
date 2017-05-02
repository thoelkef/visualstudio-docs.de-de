---
title: "Ung&#252;ltiges Ersetzungsargument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Ung&#252;ltiges Ersetzungsargument
Es wurde versucht, `JSON.stringify` mit einem Argument aufzurufen, das ungültig ist.  Das `replacer`\-Argument muss eine Funktion oder ein Array sein.  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie das `replacer`\-Argument in eine Funktion oder ein Array.  
  
## Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `memberfilter` ein Objekt statt einer Funktion oder eines Arrays ist.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## Siehe auch  
 [JSON\-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript\-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)