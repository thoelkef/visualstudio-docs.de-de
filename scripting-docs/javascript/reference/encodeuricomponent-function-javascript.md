---
title: "encodeURIComponent-Funktion (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent-Methode"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent-Funktion (JavaScript)
Codiert eine Textzeichenfolge als gültige Komponente eines URIs \(Uniform Resource Identifier\).  
  
## Syntax  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## Hinweise  
 Das erforderliche `encodedURIString`\-Argument ist ein Wert, der eine codierte URI\-Komponente darstellt.  
  
 Die `encodeURIComponent`\-Funktion gibt einen codierten URI zurück.  Wenn Sie das Ergebnis an `decodeURIComponent` übergeben, wird die ursprüngliche Zeichenfolge zurückgegeben.  Da durch die `encodeURIComponent`\-Funktion sämtliche Zeichen codiert werden, sollten Sie vorsichtig vorgehen, wenn die Zeichenfolge einen Pfad wie \/Ordner1\/Ordner2\/default.html darstellt.  Da die Schrägstriche codiert werden, sind sie ungültig, wenn sie als Anforderung an einen Webserver gesendet werden.  Verwenden Sie die `encodeURI`\-Funktion, wenn die Zeichenfolge mehr als eine URI\-Komponente enthält.  
  
## Beispiel  
 Im folgenden Code wird eine URI\-Komponente zuerst codiert und dann decodiert.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
## Siehe auch  
 [decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)