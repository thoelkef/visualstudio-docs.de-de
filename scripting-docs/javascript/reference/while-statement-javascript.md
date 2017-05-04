---
title: "while-Anweisung (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Schleifenstrukturen, while-Anweisungen"
  - "while-Anweisung"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while-Anweisung (JavaScript)
Führt eine Anweisung oder eine Reihe von Anweisungen aus, bis eine bestimmte Bedingung `false` ist.  
  
## Syntax  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Parameter  
 `expression`  
 Erforderlich.  Ein boolescher Ausdruck, der vor jeder Schleifeniteration überprüft wird.  Wenn `expression` `true` ist, wird die Schleife ausgeführt.  Wenn `expression` `false` ist, wird die Schleife beendet.  
  
 `statements`  
 Dies ist optional.  Eine oder mehrere Anweisungen, die ausgeführt werden sollen, wenn `expression` `true` ist.  
  
## Hinweise  
 Die `while`\-Anweisung überprüft `expression` vor der ersten Ausführung einer Schleife.  Lautet der Wert für `expression` bereits zu diesem Zeitpunkt `false`, wird die Schleife nie ausgeführt.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `while`\-Anweisung.  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue\-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [do...while\-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)