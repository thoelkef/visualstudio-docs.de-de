---
title: "return-Anweisung (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function-Anweisung"
  - "return-Anweisung"
  - "return-Anweisung, Beenden von Funktionen im Skript"
  - "return-Anweisung, Syntax"
  - "Abbruchsausführung"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return-Anweisung (JavaScript)
Beendet die aktuelle Funktion und gibt einen Wert von dieser Funktion zurück.  
  
## Syntax  
  
```  
  
return[(][expression][)];   
```  
  
## Hinweise  
 Das optionale *expression*\-Argument ist der von der Funktion zurückzugebende Wert.  Ohne Angabe dieses Arguments gibt die Funktion keinen Wert zurück.  
  
 Sie verwenden die `return`\-Anweisung, wenn die Ausführung einer Funktion beendet und der Wert von *expression* zurückgegeben werden soll.  Wird *expression* ausgelassen bzw. keine `return`\-Anweisung in der Funktion ausgeführt, wird dem Ausdruck, durch den die aktuelle Funktion aufgerufen wurde, der Wert "undefined" zugewiesen.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `return`\-Anweisung.  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `return`\-Anweisung zur Rückgabe einer Funktion.  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)