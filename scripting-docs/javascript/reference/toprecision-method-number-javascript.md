---
title: "toPrecision-Methode (Zahl) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision-Methode"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision-Methode (Zahl) (JavaScript)
Stellt eine Zahl entweder in Exponentialnotation oder in Festkommanotation mit einer angegebenen Anzahl von Stellen dar.  
  
## Syntax  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## Parameter  
 `numObj`  
 Erforderlich.  Ein `Number`\-Objekt.  
  
 `precision`  
 Optional.  Die Anzahl von signifikanten Ziffern.  Muss im Bereich 1 bis \(einschließlich\) 21 liegen.  
  
## Rückgabewert  
 Für Zahlen in Exponentialnotation werden `precision` – 1 Ziffern nach dem Komma zurückgegeben.  Für Zahlen in Festkommanotation werden `precision` signifikante Ziffern zurückgegeben.  
  
 Wenn `precision` nicht angegeben oder **undefined** ist, wird stattdessen die **toString**\-Methode aufgerufen.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung von `toPrecision` veranschaulicht.  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## Siehe auch  
 [toFixed\-Methode \(Zahl\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential\-Methode \(Zahl\)](../../javascript/reference/toexponential-method-number-javascript.md)