---
title: "$1...$9-Eigenschaften (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$1...$9"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$1...$9-Eigenschaften"
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# $1...$9-Eigenschaften (RegExp) (JavaScript)
Die neun zuletzt gespeicherten Teile zurückgeben, die während des Mustervergleichs gefunden wurden.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
RegExp.$n   
```  
  
## Parameter  
 `RegExp`  
 Immer das globale `RegExp`\-Objekt.  
  
 `n`  
 Eine beliebige ganze Zahl zwischen 1 und 9.  
  
## Hinweise  
 Die Werte der **$1...$9**\-Eigenschaften werden immer dann geändert, wenn eine in Klammern gesetzte Übereinstimmung gefunden wurde.  In einem Muster eines regulären Ausdrucks können beliebig viele in Klammern gesetzte untergeordnete Zeichenfolgen angegeben werden, es werden jedoch nur die neun zuletzt gefundenen gespeichert.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Suche mit einem regulären Ausdruck durchgeführt.  Es werden Übereinstimmungen und teilweise Übereinstimmungen aus dem globalen `RegExp`\-Objekt angezeigt.  Die teilweisen Übereinstimmungen sind in Klammern gesetzte Übereinstimmungen, die in den `$1…$9`\-Eigenschaften enthalten sind.  Im Beispiel werden außerdem Übereinstimmungen und teilweise Übereinstimmungen aus dem Array angezeigt, das von der `exec`\-Methode zurückgegeben wird.  
  
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
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## Siehe auch  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)