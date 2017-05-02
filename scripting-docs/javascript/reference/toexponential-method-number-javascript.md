---
title: "toExponential-Methode (Zahl) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential-Methode"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential-Methode (Zahl) (JavaScript)
Stellt eine Zahl in Exponentialnotation dar.  
  
## Syntax  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## Parameter  
 `numObj`  
 Erforderlich.  Ein **Number**\-Objekt.  
  
 `fractionDigits`  
 Optional.  Die Anzahl von Ziffern nach dem Komma.  Muss im Bereich 0 bis \(einschließlich\) 20 liegen.  
  
## Rückgabewert  
 Gibt eine Zeichenfolgenentsprechung einer Zahl in exponentieller Notation zurück.  Die Zeichenfolge enthält eine Ziffer vor dem Komma, und kann `fractionDigits`\-Ziffern nach dem Komma enthalten.  
  
 Wenn `fractionDigits` nicht angegeben wird, gibt die `toExponential`\-Methode so viele Ziffern zurück, wie zur eindeutigen Angabe der Zahl erforderlich sind.  
  
## Beispiel  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## Siehe auch  
 [toFixed\-Methode \(Zahl\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision\-Methode \(Zahl\)](../../javascript/reference/toprecision-method-number-javascript.md)