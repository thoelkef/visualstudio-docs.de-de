---
title: "decodeURIComponent-Funktion (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent-Methode"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent-Funktion (JavaScript)
Ruft die decodierte Version einer codierten Komponente eines URIs \(Uniform Resource Identifier\) ab.  
  
## Syntax  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## Hinweise  
 Das erforderliche `encodedURIString`\-Argument ist ein Wert, der eine codierte URI\-Komponente darstellt.  
  
 Eine URI\-Komponente ist Teil eines vollständigen URIs.  
  
 Wenn `encodedURIString` ungültig ist, tritt ein Fehler vom Typ URIError auf.  
  
## Beispiel  
 Der folgende Code codiert zuerst und decodiert dann einen URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
## Siehe auch  
 [decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI\-Funktion](../../javascript/reference/encodeuri-function-javascript.md)