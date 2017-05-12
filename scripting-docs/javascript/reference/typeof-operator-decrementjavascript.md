---
title: "typeof-Operator (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof-Operator"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof-Operator (JavaScript)
Gibt eine Zeichenfolge zurück, die den Datentyp eines Ausdrucks angibt.  
  
## Syntax  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## Hinweise  
 Das *expression*\-Argument ist ein beliebiger Ausdruck, für den Typinformationen ermittelt werden.  
  
 Der Operator `typeof` gibt die Typinformationen als Zeichenfolge zurück.  Es gibt sechs mögliche Rückgabewerte für `typeof`: "number", "string", "boolean", "object", "function" und "undefined".  
  
 In der `typeof`\-Syntax sind die Klammern optional.  
  
## Beispiel  
 Das folgende Beispiel testet den Datentyp der Variablen.  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## Beispiel  
 Im folgenden Beispiel wird überprüft, ob deklarierte und nicht deklarierte Variablen des Datentyps `undefined` vorhanden sind.  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Array.isArray\-Funktion](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf\-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined\-Konstante](../../javascript/reference/undefined-constant-javascript.md)   
 [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md)   
 [Datentypen](../../javascript/data-types-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)