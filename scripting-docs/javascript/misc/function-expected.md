---
title: "Funktion erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Funktion erwartet
Sie haben entweder versucht, eine der **Funktionsprototyp**\-Methoden auf einem Objekt aufzurufen, das kein `Function`\-Objekt war, oder Sie haben ein Objekt in einem Funktionsaufrufkontext verwendet.  Beispielsweise generiert der folgende Code diesen Fehler, weil **example** keine Funktion ist.  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie nur **Funktionsprototyp**\-Methoden auf `Function`\-Objekten auf.  
  
-   Stellen Sie sicher, denn Funktionsaufrufoperator `()` für den Aufruf von Funktionen zu verwenden.  
  
## Siehe auch  
 [Function\-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype\-Eigenschaft \(Objekt\)](../../javascript/reference/prototype-property-object-javascript.md)