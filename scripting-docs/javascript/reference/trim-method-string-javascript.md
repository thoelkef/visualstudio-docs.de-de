---
title: "trim-Methode (String) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "trim-Methode"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim-Methode (String) (JavaScript)
Entfernt die führenden und nachfolgenden Leerstellen\- und Zeilenabschlusszeichen aus einer Zeichenfolge.  
  
## Syntax  
  
```  
  
stringObj.trim()  
```  
  
## Parameter  
 `stringObj`  
 Erforderlich.  Ein `String`\-Objekt oder Zeichenfolgenliteral.  Diese Zeichenfolge wird nicht von der `trim`\-Methode geändert.  
  
## Rückgabewert  
 Die ursprüngliche Zeichenfolge, aus der die führenden und nachfolgenden Leerstellen\- und Zeilenabschlusszeichen entfernt wurden.  
  
## Hinweise  
 Die entfernten Zeichen umfassen Leerzeichen, Tabulatorzeichen, Seitenvorschübe, Wagenrückläufe und Zeilenvorschübe.  Eine umfassende Liste von Leerstellen\- und Zeilenabschlusszeichen finden Sie unter [Sonderzeichen](../../javascript/advanced/special-characters-javascript.md).  
  
 Ein Beispiel für die Implementierung einer eigenen trim\-Methode finden Sie unter [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `trim`\-Methode veranschaulicht.  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Sonderzeichen](../../javascript/advanced/special-characters-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)   
 [Beispiel\-App für Bildlauf, Schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)