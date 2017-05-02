---
title: "throw-Anweisung (JavaScript) | Microsoft Docs"
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
  - "throw_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Fehlerbehandlung, throw-Anweisung"
  - "throw-Anweisung"
ms.assetid: 75cbade0-fb81-4ffe-b187-b71be380bb05
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# throw-Anweisung (JavaScript)
Generiert einen Fehlerzustand, der von einer `try...catch...finally`\-Anweisung behandelt werden kann.  
  
## Syntax  
  
```  
throw exception   
```  
  
## Hinweise  
 Das erforderliche `exception`\-Argument kann ein beliebiger Ausdruck sein.  
  
 Im folgenden Beispiel wird ein Fehler innerhalb eines `try`\-Blocks ausgelöst und wird im `catch`\-Block abgefangen.  
  
```javascript  
try {  
        throw new Error(200, "x equals zero");  
}  
catch (e) {  
    document.write(e.message);  
}  
  
// Output: x equals zero.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../includes/jsv5-md.md)]  
  
## Siehe auch  
 [try...catch...finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error\-Objekt](../../javascript/reference/error-object-javascript.md)