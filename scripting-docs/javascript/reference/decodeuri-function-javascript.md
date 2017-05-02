---
title: "decodeURI-Funktion (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI-Methode"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI-Funktion (JavaScript)
Ruft die decodierte Version eines codierten URIs \(Uniform Resource Identifier\) ab.  
  
## Syntax  
  
```  
decodeURI(URIstring)  
```  
  
## Hinweise  
 Das erforderliche `URIstring`\-Argument ist ein Wert, der einen codierten URI darstellt.  
  
 Verwenden Sie die `decodeURI`\-Funktion statt der veralteten `unescape`\-Funktion.  
  
 Die `decodeURI`\-Funktion gibt eine Zeichenfolge zurück.  
  
 Wenn `URIString` ungültig ist, tritt ein Fehler vom Typ URIError auf.  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Beispiel  
 Im folgenden Code wird eine URI\-Komponente zuerst codiert und dann decodiert.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [decodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI\-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global\-Objekt](../../javascript/reference/global-object-javascript.md)