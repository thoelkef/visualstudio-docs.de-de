---
title: "const-Anweisung (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Deklarieren von Variablen, const-Anweisung"
  - "Const-Anweisung"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const-Anweisung (JavaScript)
Deklariert eine Block\-bewertete Variable mit einem konstanten Wert.  
  
## Syntax  
  
```  
const constant1 = value1  
```  
  
#### Parameter  
 `constant1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## Hinweise  
 Verwenden Sie die `const`\-Anweisung zum Deklarieren einer Variablen mit einem konstanten Wert, deren Bereich auf den Block beschränkt ist, in dem sie deklariert wurde.  Der Wert dieser Variablen kann nicht geändert werden.  
  
 Eine Variable, die mit `const` deklariert wird, muss initialisiert werden, wenn sie deklariert wurde.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `const`\-Anweisung.  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [let\-Anweisung](../../javascript/reference/let-statement-javascript.md)   
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)