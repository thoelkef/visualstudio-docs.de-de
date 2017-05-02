---
title: "for...of-Anweisung (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# for...of-Anweisung (JavaScript)
Führt eine oder mehrere Anweisungen für jeden Wert eines Iterators aus, der von einem iterable\-Wert abgerufen wurde.  
  
## Syntax  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## Parameter  
 `variable`  
 Erforderlich.  Eine Variable, die einen beliebigen Eigenschaftswert von `object` sein kann.  
  
 `object`  
 Erforderlich.  Ein iterable\-Objekt, wie z. B. ein `Array`, `Map`, `Set`, oder ein Objekt, das die [Iterator\-Schnittstellen](http://msdn.microsoft.com/de-de/3692355a-a703-4d43-8fb5-c03b4b7e8db1) implementiert.  
  
 `statements`  
 Optional.  Eine oder mehrere auszuführende Anweisungen für jeden Wert von `object`.  Kann eine Verbundanweisung sein.  
  
## Hinweise  
 Am Anfang jeder Iteration einer Schleife, ist der Wert der `variable` der nächste Eigenschaftswert der `object`.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...of`\-Anweisung in einem Array.  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...of`\-Anweisung in einem `Map`Objekt.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
## Siehe auch  
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)