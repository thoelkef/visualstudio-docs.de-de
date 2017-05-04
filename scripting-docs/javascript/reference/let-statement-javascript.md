---
title: "let-Anweisung (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let-Anweisung"
  - "Deklarieren von Variablen, let-Anweisung"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let-Anweisung (JavaScript)
Deklariert eine Block\-bewertete Variable.  
  
## Syntax  
  
```  
let variable1 = value1  
```  
  
#### Parameter  
 `variable1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## Hinweise  
 Verwenden Sie die `let`\-Anweisung zum Deklarieren einer Variablen, deren Bereich auf den Block beschränkt ist, in dem sie deklariert wurde.  Den Variablen können in der Deklaration oder später im Skript Werte zugewiesen werden.  
  
 Eine Variable, die mit `let` deklariert wird, kann nicht vor ihrer Deklaration verwendet werden, andernfalls tritt ein Fehler auf.  
  
 Wenn Sie die Variable in der `let`\-Anweisung nicht initialisieren, wird ihr automatisch der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Wert `undefined` zugewiesen.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `let`\-Anweisung.  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [const\-Anweisung](../../javascript/reference/const-statement-javascript.md)   
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)