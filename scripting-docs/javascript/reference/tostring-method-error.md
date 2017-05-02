---
title: "toString-Methode (Fehler) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString-Methode (Fehler)
Gibt eine Zeichenfolgendarstellung eines Fehlers zurück.  
  
## Syntax  
  
```  
  
error.toString()  
```  
  
## Parameter  
 `date`  
 Erforderlich.  Der Fehler, der als Zeichenfolge dargestellt werden soll.  
  
## Rückgabewert  
 Gibt "Error:" zurück sowie die Fehlermeldung.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `toString`\-Methode mit einem Fehler.  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]