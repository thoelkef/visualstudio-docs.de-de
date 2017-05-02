---
title: "Math.acosh-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.acosh-Funktion (JavaScript)
Gibt den hyperbolischen Arkuskosinus \(oder den umgekehrten hyperbolischen Kosinus\) einer Zahl zurück.  
  
## Syntax  
  
```  
Math.acosh(number)  
```  
  
#### Parameter  
 Das erforderliche `number`\-Argument ist ein numerischer Ausdruck.  
  
## Rückgabewert  
 Der umgekehrte hyperbolische Kosinus des `number`\-Arguments im Bogenmaß.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung der `acosh`\-Funktion veranschaulicht.  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## Hinweise  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
## Siehe auch  
 [Math.acos\-Funktion](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin\-Funktion](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan\-Funktion](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos\-Funktion](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin\-Funktion](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan\-Funktion](../../javascript/reference/math-tan-function-javascript.md)   
 [Math\-Objekt](../../javascript/reference/math-object-javascript.md)