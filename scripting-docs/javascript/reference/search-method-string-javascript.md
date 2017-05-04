---
title: "search-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search-Methode"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search-Methode (String) (JavaScript)
Findet die erste Übereinstimmung mit der Teilzeichenfolge in einem regulären Ausdruck.  
  
## Syntax  
  
```  
  
stringObj.search(rgExp)   
```  
  
## Parameter  
 `stringObj`  
 Erforderlich.  Das `String`\-Objekt oder Zeichenfolgenliteral, in dem die Suche ausgeführt werden soll.  
  
 `rgExp`  
 Erforderlich.  Eine Instanz eines **Regular Expression**\-Objekts, in der das Muster des regulären Ausdrucks und anwendbare Flags enthalten sind.  
  
## Rückgabewert  
 Wenn eine Übereinstimmung gefunden wird, gibt die **search**\-Methode einen ganzzahligen Wert zurück, der den Offset vom Anfang der Zeichenfolge angibt, in der die erste Übereinstimmung auftritt.  Wird keine Übereinstimmung gefunden, wird der Wert \-1 zurückgegeben.  
  
## Hinweise  
 Sie können auch das Flag `i` festlegen, damit bei der Suche nicht zwischen Groß\- und Kleinschreibung unterschieden wird.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der **search**\-Methode veranschaulicht.  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [exec\-Methode \(regulärer Ausdruck\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match\-Methode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace\-Methode \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test\-Methode \(regulärer Ausdruck\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/de-de/3b62e27c-4f07-4726-a95b-6e841807bfaf)