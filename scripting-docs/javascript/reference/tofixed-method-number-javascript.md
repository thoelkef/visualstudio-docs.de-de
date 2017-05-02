---
title: "toFixed-Methode (Zahl) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed-Methode"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed-Methode (Zahl) (JavaScript)
Stellt eine Zahl in Festkommanotation dar.  
  
## Syntax  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Parameter  
 `numObj`  
 Ein `Number`\-Objekt ist erforderlich.  
  
 `fractionDigits`  
 Dies ist optional.  Die Anzahl der Ziffern nach dem Komma.  Muss im Bereich 0 bis \(einschließlich\) 20 liegen.  
  
## Rückgabewert  
 Gibt eine Zeichenfolgendarstellung einer Zahl in Festkommanotation zurück, die `fractionDigits` Ziffern nach dem Dezimaltrennzeichen enthält.  
  
 Wenn `fractionDigits` oder **undefined** nicht angegeben wird, ist der Standardwert null.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung von `toFixed` veranschaulicht.  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## Siehe auch  
 [toExponential\-Methode \(Zahl\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision\-Methode \(Zahl\)](../../javascript/reference/toprecision-method-number-javascript.md)