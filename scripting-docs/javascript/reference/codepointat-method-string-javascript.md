---
title: "codePointAt-Methode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# codePointAt-Methode (String) (JavaScript)
Gibt den Codepunkt eines Unicode\-UTF\-16\-Zeichens zurück.  
  
## Syntax  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### Parameter  
 `stringObj`  
 Erforderlich.  Das String\-Objekt.  
  
 `pos`  
 Erforderlich.  Die Position des Zeichens.  
  
## Hinweise  
 Diese Methode gibt die Codepunktwerte, einschließlich astraler Codepunkte \(mit mehr als vier Hexadezimalwerten\), für alle UTF\-16\-Zeichen zurück.  
  
 Wenn `pos` kleiner als 0 oder größer als die Größe der Zeichenfolge ist, ist der Rückgabewert `undefined`.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `codePointAt`\-Methode gezeigt.  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]