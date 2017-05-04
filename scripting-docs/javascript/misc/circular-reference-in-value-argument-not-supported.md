---
title: "Zirkelverweis im Wertargument nicht unterst&#252;tzt | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Zirkelverweis im Wertargument nicht unterst&#252;tzt
Es wurde versucht, `JSON.stringify` mit einem ungültigen Argument aufzurufen.  Das `value`\-Argument, ein Array oder Objekt, enthält einen Zirkelbezug.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Zirkelbezug aus dem Argument.  
  
## Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `john` über einen Verweis auf `mary` verfügt und `mary` einen Verweis auf `john` enthält.  um den Zirkelverweis zu entfernen, entfernen Sie die `brother`\-Eigenschaft aus dem `mary`\-Objekt oder die `sister`\-Eigenschaft aus dem `john`\-Objekt bzw. machen Sie die Festlegung rückgängig.  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## Siehe auch  
 [JSON\-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript\-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)