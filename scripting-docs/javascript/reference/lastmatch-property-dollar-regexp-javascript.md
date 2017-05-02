---
title: "lastMatch-Eigenschaft ($&amp;) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastMatch-Eigenschaft ($%)"
  - "lastMatch-Eigenschaft ($&)"
ms.assetid: d223836d-5235-48a5-a926-d20764ad3f14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# lastMatch-Eigenschaft ($&amp;) (RegExp) (JavaScript)
Gibt die letzten übereinstimmenden Zeichen einer beliebigen Suche mit einem regulären Ausdruck zurück.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
RegExp.lastMatch  
```  
  
## Hinweise  
 Das mit dieser Eigenschaft verknüpfte Objekt ist immer das globale `RegExp`\-Objekt.  
  
 Der Anfangswert der `lastMatch`\-Eigenschaft ist eine leere Zeichenfolge.  Der Wert der `lastMatch`\-Eigenschaft wird stets geändert, wenn eine Übereinstimmung gefunden wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `lastMatch`\-Eigenschaft veranschaulicht:  
  
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
 [lastParen\-Eigenschaft \($\+\) \(RegExp\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [leftContext\-Eigenschaft \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext\-Eigenschaft \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)