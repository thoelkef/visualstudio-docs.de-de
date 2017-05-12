---
title: "repeat-Methode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# repeat-Methode (String) (JavaScript)
Gibt ein neues String\-Objekt mit einem Wert zurück, der gleich der ursprünglichen Zeichenfolge in der angegebenen Anzahl von Wiederholungen ist.  
  
## Syntax  
  
```  
stringObj.repeat(count);  
```  
  
#### Parameter  
 `stringObj`  
 Erforderlich.  Das String\-Objekt.  
  
 `count`  
 Erforderlich.  Die Anzahl der Wiederholungen der ursprünglichen Zeichenfolge in der zurückgegebenen Zeichenfolge.  
  
## Ausnahmen  
 Diese Methode löst einen RangeError aus, wenn und nur wenn das Argument negativ oder plus unendlich ist.  
  
## Hinweise  
 Die `repeat`\-Methode verkettet die ursprüngliche Zeichenfolge mit der neuen Zeichenfolge, und zwar so oft, wie von `count` angegeben.  
  
 Diese Methode löst einen Fehler aus, wenn `count` keine positive Zahl kleiner als `Infinity` ist.  
  
## Beispiel  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]