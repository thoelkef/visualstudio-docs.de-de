---
title: "RegExp-Objekt (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp-Objekt"
  - "RegExp-Objekt, Übersicht"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp-Objekt (JavaScript)
Ein systeminternes globales Objekt, das die Informationen zu den Ergebnissen des übereinstimmenden Musters des regulären Ausdrucks speichert.  
  
## Syntax  
  
```  
  
RegExp.property   
```  
  
## Hinweise  
 Das erforderliche *Eigenschaftargument* kann eine der `RegExp`\-Objekteigenschaften sein.  
  
 Das `RegExp`\-Objekt kann nicht direkt erstellt werden, ist jedoch stets zur Verwendung verfügbar.  Bis eine Suche mit einem regulärem Ausdruck erfolgreich beendet werden kann, haben die einzelnen Eigenschaften des `RegExp`\-Objekts folgende Startwerte:  
  
|Eigenschaft|Kurznotation|Anfangswert|  
|-----------------|------------------|-----------------|  
|index||\-1|  
|input|$\_|Leere Zeichenfolge.|  
|lastIndex||\-1|  
|lastMatch|$&|Leere Zeichenfolge.|  
|lastParen|$\+|Leere Zeichenfolge.|  
|leftContext|$\`|Leere Zeichenfolge.|  
|rightContext|$'|Leere Zeichenfolge.|  
|$1 \- $9|$1 \- $9|Leere Zeichenfolge.|  
  
 Die Eigenschaften haben solange "undefined" als Wert, bis eine erfolgreiche Suche mit einem regulären Ausdruck abgeschlossen wurde.  
  
 Das globale `RegExp`\-Objekt darf nicht mit dem **Regular Expression**\-Objekt verwechselt werden.  Es sieht so aus, als wären es dieselben Objekte, sie sind jedoch verschieden.  Die Eigenschaften des globalen `RegExp`\-Objekts enthalten fortwährend aktualisierte Informationen über jede aufgetretene Übereinstimmung, während die Eigenschaften des **Regular Expression**\-Objekts nur Informationen über die Übereinstimmungen enthalten, die bei einer einzigen Instanz von **Regular Expression** auftreten.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Suche mit einem regulären Ausdruck durchgeführt.  Es werden Übereinstimmungen und teilweise Übereinstimmungen aus dem globalen `RegExp`\-Objekt und aus dem Array angezeigt, das von der `exec`\-Methode zurückgegeben wird.  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## Eigenschaften  
 [$1...$9\-Eigenschaften](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index\-Eigenschaft](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input\-Eigenschaft](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex\-Eigenschaft](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch\-Eigenschaft](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen\-Eigenschaft](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext\-Eigenschaft](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext\-Eigenschaft](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## Methoden  
 Für das `RegExp`\-Objekt sind keine Methoden verfügbar.  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)