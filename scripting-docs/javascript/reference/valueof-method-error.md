---
title: "valueOf-Methode (Fehler) | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf-Methode (Fehler)
Gibt den Zeichenfolgenwert eines Fehlers zurück.  
  
## Syntax  
  
```  
  
error.valueOf()  
```  
  
#### Parameter  
 Das `error`\-Objekt ist eine beliebige Instanz eines Fehlers.  
  
## Rückgabewert  
 Die Zeichenfolge "Fehler: " mit anschließender Fehlermeldung.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `valueOF`\-Methode mit einem Datum.  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]