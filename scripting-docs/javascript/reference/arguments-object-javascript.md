---
title: "arguments-Objekt (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments-Objekt"
  - "Argumente, arguments-Objekt"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments-Objekt (JavaScript)
Ein Objekt, das die Argumente der gegenwärtig ausgeführten Funktion und die Funktionen darstellt, die das Objekt aufgerufen hat.  
  
## Syntax  
  
```  
[function.]arguments[n]  
```  
  
## Parameter  
 *Funktion*  
 Dies ist optional.  Der Name des aktuell ausgeführten `Function`\-Objekts.  
  
 *n*  
 Erforderlich.  Der nullbasierte Index der Argumentwerte, die an das `Function`\-Objekt übergeben werden.  
  
## Hinweise  
 Ein **arguments**\-Objekt kann nicht explizit erstellt werden.  Das **arguments**\-Objekt ist nur verfügbar, wenn die Ausführung einer Funktion beginnt.  Das **arguments**\-Objekt der Funktion ist kein Array, auf die einzelnen Argumente kann jedoch auf dieselbe Weise wie auf Arrayelemente zugegriffen werden.  Der Index *n* ist tatsächlich ein Verweis auf eine der **0** ***n***\-Eigenschaften des **arguments**\-Objekts.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des **arguments**\-Objekts.  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [0...n\-Eigenschaften \(Argumente\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee\-Eigenschaft \(Argumente\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length\-Eigenschaft \(Arguments\)](../../javascript/reference/length-property-arguments-javascript.md)