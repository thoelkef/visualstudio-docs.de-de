---
title: "arguments-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs"
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
  - "Argumente, arguments-Eigenschaft"
  - "Arguments-Eigenschaft"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments-Eigenschaft (Funktion) (JavaScript)
Ruft die Argumente für das aktuell ausgeführte `Function`\-Objekt ab.  
  
## Syntax  
  
```  
  
function.arguments  
```  
  
## Hinweise  
 Das `function`\-Argument ist der Name der aktuell ausgeführten Funktion und kann ausgelassen werden.  
  
 Diese Eigenschaft ermöglicht es einer Funktion, eine variable Anzahl von Argumenten zu verarbeiten.  Die **length**\-Eigenschaft des `arguments`\-Objekts enthält die Anzahl der an die Funktion übergebenen Argumente.  Auf die einzelnen im `arguments`\-Objekt enthaltenen Argumente kann auf dieselbe Weise zugegriffen werden wie auf Arrayelemente.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `arguments`\-Eigenschaft veranschaulicht:  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Siehe auch  
 [arguments\-Objekt](../../javascript/reference/arguments-object-javascript.md)   
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)