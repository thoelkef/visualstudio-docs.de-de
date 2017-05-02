---
title: "length-Eigenschaft (Arguments) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length-Eigenschaft"
  - "length-Eigenschaft (Arguments)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length-Eigenschaft (Arguments) (JavaScript)
Gibt die tatsächliche Anzahl der Argumente zurück, die von der aufrufenden Routine an eine Funktion übergeben wurden.  
  
## Syntax  
  
```  
[function.]arguments.length  
```  
  
## Hinweise  
 Das optionale *function*\-Argument ist der Name des `Function`\-Objekts, das derzeit ausgeführt wird.  
  
 Die **length**\-Eigenschaft des **arguments**\-Objekts wird vom Skriptmodul mit der tatsächlichen Anzahl von Argumenten, die an ein `Function`\-Objekt übergeben wurden, zu Beginn der Ausführung dieser Funktion initialisiert.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **length**\-Eigenschaft des **arguments**\-Objekts.  Um das Beispiel besser zu verstehen, können Sie zusätzlich zu den zwei erwarteten Argumenten weitere Argumente an die Funktion übergeben:  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [arguments\-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Function\-Objekt](../../javascript/reference/function-object-javascript.md)  
  
## Siehe auch  
 [arguments\-Eigenschaft \(Funktion\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length\-Eigenschaft \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length\-Eigenschaft \(String\)](../../javascript/reference/length-property-string-javascript.md)