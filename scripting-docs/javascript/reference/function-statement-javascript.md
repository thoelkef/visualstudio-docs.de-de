---
title: "function-Anweisung (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Deklarieren von Funktionen"
  - "Deklarieren von Funktionen, Syntax"
  - "function-Anweisung"
  - "new-Operator"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function-Anweisung (JavaScript)
Deklariert eine neue Funktion.  
  
## Syntax  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## Parameter  
 `functionname`  
 Erforderlich.  Der Name der Funktion.  
  
 `arg1...argN`  
 Optional.  Eine optionale, durch Trennzeichen getrennte Liste von Argumenten, die die Funktion versteht.  
  
 `statements`  
 Optional.  Eine oder mehrere [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Anweisungen.  
  
## Hinweise  
 Verwenden Sie die `function`\-Anweisung, um eine Funktion für den späteren Gebrauch zu deklarieren.  Der in `statements` enthaltene Code wird erst ausgeführt, wenn die Funktion von anderer Stelle im Skript aus aufgerufen wird.  
  
 Die [return](../../javascript/reference/return-statement-javascript.md)\-Anweisung wird für die Rückgabe eines Werts aus der Funktion verwendet.  Sie müssen keine `return`\-Anweisung verwenden, da das Programm eine Rückgabe erzeugt, wenn es das Ende der Funktion erreicht.  Wenn keine `return`\-Anweisung in der Funktion ausgeführt wird oder die `return`\-Anweisung keinen Ausdruck hat, gibt die Funktion den Wert `undefined` zurück.  
  
> [!NOTE]
>  Wenn Sie eine Funktion aufrufen, stellen Sie sicher, die Klammern und alle erforderlichen Argumente einzuschließen.  Wird eine Funktion ohne Klammern aufgerufen, wird ein Verweis auf die Funktion zurückgegeben, die Ergebnisse der Funktion werden hingegen nicht zurückgegeben.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `function`\-Anweisung.  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## Beispiel  
 Eine Funktion kann einer Variablen zugewiesen werden.  Dies wird im folgenden Beispiel veranschaulicht.  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)