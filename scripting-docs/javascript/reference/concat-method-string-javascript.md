---
title: "concat-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat-Methode (String)"
  - "Concat-Methode"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat-Methode (String) (JavaScript)
Gibt eine Zeichenfolge zurück, die die Verkettung von zwei oder mehr Zeichenfolgen enthält.  
  
## Syntax  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## Parameter  
 `string1`  
 Erforderlich.  Das `String`\-Objekt oder \-Literal, zu dem alle anderen angegebenen Zeichenfolgen verkettet werden.  
  
 `string2,. . ., stringN`  
 Optional.  Die am Ende von `string1` anzufügenden Zeichenfolgen.  
  
## Hinweise  
 Das Ergebnis der `concat`\-Methode entspricht: `result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`.  Eine Wertänderung in einer Quell\- oder Ergebniszeichenfolge hat keine Auswirkungen auf den Wert in der anderen Zeichenfolge.  Argumente, die keine Zeichenfolge sind, werden zunächst in Zeichenfolgen konvertiert und anschließend zu `string1` verkettet.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `concat`\-Methode in Verbindung mit einer Zeichenfolge:  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [Additionsoperator \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)