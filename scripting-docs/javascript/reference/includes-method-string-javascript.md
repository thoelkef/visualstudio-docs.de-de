---
title: "includes-Methode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# includes-Methode (String) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob die übergebene Zeichenfolge im string\-Objekt enthalten ist.  
  
## Syntax  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### Parameter  
 `stringObj`  
 Erforderlich.  Das string\-Objekt für den Test.  
  
 `substring`  
 Erforderlich.  Die zu testende Zeichenfolge.  
  
 `position`  
 Optional.  Die Position des ersten Zeichens für den Test im string\-Objekt, beginnend mit 0.  
  
## Rückgabewert  
 Wenn die übergebene Zeichenfolge im string\-Objekt enthalten ist, gibt die `includes`\-Methode `true` zurück, andernfalls gibt sie `false` zurück.  
  
## Hinweise  
  
## Beispiel  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]