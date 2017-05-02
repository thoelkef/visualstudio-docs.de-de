---
title: "lastParen-Eigenschaft ($+) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastParen-Eigenschaft ($+)"
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# lastParen-Eigenschaft ($+) (RegExp) (JavaScript)
Gibt die letzte in Klammern gesetzte Teilübereinstimmung einer beliebigen Suche mit regulärem Ausdruck zurück, sofern vorhanden.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
RegExp.lastParen  
```  
  
## Hinweise  
 Das mit dieser Eigenschaft verknüpfte Objekt ist immer das globale `RegExp`\-Objekt.  
  
 Der Anfangswert der `lastParen`\-Eigenschaft ist eine leere Zeichenfolge.  Der Wert der `lastParen`\-Eigenschaft wird stets geändert, wenn eine Übereinstimmung gefunden wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `lastParen`\-Eigenschaft veranschaulicht:  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## Siehe auch  
 [$1...$9\-Eigenschaften \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index\-Eigenschaft \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input\-Eigenschaft \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex\-Eigenschaft \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch\-Eigenschaft \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext\-Eigenschaft \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext\-Eigenschaft \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)