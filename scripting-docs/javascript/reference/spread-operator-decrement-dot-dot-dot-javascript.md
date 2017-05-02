---
title: "Spread-Operator (...) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Spread-Operator (...) (JavaScript)
Ermöglicht Teilen eines Arrayliterals die Initialisierung aus einem iterierbaren Ausdruck \(z. B. einem anderen Arrayliteral\) oder einem Ausdruck das Erweitern auf mehrere Argumente \(in Funktionsaufrufen\).  
  
## Syntax  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## Parameter  
 `iterable`  
 Erforderlich.  Ein iterierbares Objekt.  
  
 `arg0ToN`  
 Dies ist optional.  Ein oder mehrere Elemente eines Arrayliterals.  
  
 `args`  
 Dies ist optional.  Ein oder mehrere Argumente für eine Funktion.  
  
## Hinweise  
 Weitere Informationen zu Iteratoren finden Sie unter [Iteratoren und Generatoren](../../javascript/advanced/iterators-and-generators-javascript.md).  Weitere Informationen zur Verwendung des Spread\-Operators als Rest\-Parameter finden Sie unter [Funktionen](../../javascript/functions-javascript.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des Spread\-Operators der Verwendung der `concat`\-Methode gegenübergestellt.  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie der Spread\-Operator in einem Funktionsaufruf verwendet wird.  In diesem Beispiel werden zwei Arrayliterale mithilfe des Spread\-Operators an die Funktion übergeben, und die Arrays werden auf mehrere Argumente erweitert.  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## Beispiel  
 Mithilfe von Spread\-Operatoren können Sie Code, der zuvor die Verwendung von `apply` erforderte, vereinfachen.  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)