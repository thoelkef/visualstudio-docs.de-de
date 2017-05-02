---
title: "encodeURI-Funktion (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI-Methode"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI-Funktion (JavaScript)
Codiert eine Textzeichenfolge als gültigen URI \(Uniform Resource Identifier\).  
  
## Syntax  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## Hinweise  
 Das erforderliche `URIString`\-Argument ist ein Wert, der einen codierten URI darstellt.  
  
 Die `encodeURI`\-Funktion gibt einen codierten URI zurück.  Wenn Sie das Ergebnis an `decodeURI` übergeben, wird die ursprüngliche Zeichenfolge zurückgegeben.  Die folgenden Zeichen werden von der `encodeURI`\-Funktion nicht codiert: ":", "\/", ";" und "?".  Verwenden Sie `encodeURIComponent`, um diese Zeichen zu codieren.  
  
## Beispiel  
 Der folgende Code codiert zuerst und decodiert dann einen URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
## Siehe auch  
 [decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)