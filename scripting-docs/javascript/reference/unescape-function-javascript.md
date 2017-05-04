---
title: "unescape-Funktion (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape-Methode"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape-Funktion (JavaScript)
Decodiert `String`\-Objekte, die mit der `escape`\-Funktion codiert wurden.  Veraltet.  
  
## Syntax  
  
```  
unescape(charString)   
```  
  
## Hinweise  
 Das erforderliche `charString`\-Argument ist ein zu decodierendes `String`\-Objekt oder Literal.  
  
 Die `unescape`\-Funktion gibt einen Zeichenfolgenwert zurück, der den Inhalt von `charstring` enthält.  Alle im hexadezimalen Format %*xx* codierten Zeichen werden durch ihre ASCII\-Zeichensatzäquivalente ersetzt.  
  
 Im Format **%u** *xxxx* codierte Zeichen \(Unicodezeichen\) werden durch Unicodezeichen mit hexadezimaler Codierung *xxxx* ersetzt.  
  
> [!NOTE]
>  Die `unescape`\-Funktion sollte nicht zum Decodieren von Uniform Resource Identifiers \(URIs\) verwendet werden.  Verwenden Sie stattdessen die `decodeURI`\-Funktion und die `decodeURIComponent`\-Funktion.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Siehe auch  
 [decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape\-Funktion](../../javascript/reference/escape-function-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)