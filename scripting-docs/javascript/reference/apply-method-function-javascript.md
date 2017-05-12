---
title: "apply-Methode (Funktion) (JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply-Methode"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# apply-Methode (Funktion) (JavaScript)
Ruft die Funktion auf und ersetzt das angegebene Objekt für den `this`\-Wert der Funktion und das angegebene Array für die Argumente der Funktion.  
  
## Syntax  
  
```  
apply([thisObj[,argArray]])  
```  
  
## Parameter  
 `thisObj`  
 Optional.  Das Objekt, das als `this`\-Objekt verwendet werden soll.  
  
 `argArray`  
 Optional.  Eine Gruppe von Argumenten, die an die Funktion übergeben werden sollen.  
  
## Hinweise  
 Wenn `argArray` kein gültiges Objekt ist, tritt ein "Objekt erwartet"\-Fehler auf.  
  
 Wenn weder `argArray` noch `thisObj` angegeben werden, wird das originale `this`\-Objekt als `thisObj` verwendet, und es werden keine Argumente übergeben.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung der Methode veranschaulicht.  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [Function\-Objekt](../../javascript/reference/function-object-javascript.md)