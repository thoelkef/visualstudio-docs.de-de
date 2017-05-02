---
title: "String.fromCharCode-Funktion (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt-Methode"
  - "Zeichen, aus Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode-Funktion (JavaScript)
Gibt eine Zeichenfolge aus einer Reihe von Unicode\-Zeichenwerten zurück.  
  
## Syntax  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## Parameter  
 `String`  
 Erforderlich.  Das `String`\-Objekt.  
  
 `code1`, . . . , `codeN`  
 Optional.  Eine Reihe von Unicodezeichenwerten, die in eine Zeichenfolge konvertiert werden.  Wenn keine Argumente angegeben werden, wird als Ergebnis eine leere Zeichenfolge zurückgegeben.  
  
## Hinweise  
 Sie rufen diese Funktion auf dem `String`\-Objekt anstatt auf einer Zeichenfolgeninstanz auf.  
  
 Im folgenden Beispiel wird die Verwendung dieser Methode gezeigt:  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [charCodeAt\-Methode \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)