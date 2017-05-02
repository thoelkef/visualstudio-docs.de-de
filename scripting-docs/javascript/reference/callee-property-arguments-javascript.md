---
title: "callee-Eigenschaft (Argumente) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee-Eigenschaft"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee-Eigenschaft (Argumente) (JavaScript)
Gibt das ausgeführte `Function`\-Objekt zurück, d. h. den Textkörper des angegebenen `Function`\-Objekts.  
  
## Syntax  
  
```  
[function.]arguments.callee  
```  
  
## Hinweise  
 Das optionale *function*\-Argument ist der Name des `Function`\-Objekts, das derzeit ausgeführt wird.  
  
 Die `callee`\-Eigenschaft ist ein Member des **arguments**\-Objekts, das erst verfügbar wird, wenn die zugehörige Funktion ausgeführt wird.  
  
 Der Anfangswert der `callee`\-Eigenschaft entspricht dem derzeit ausgeführten `Function`\-Objekt.  Dies ermöglicht die rekursive Verwendung anonymer Funktionen.  
  
## Beispiel  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [arguments\-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Function\-Objekt](../../javascript/reference/function-object-javascript.md)  
  
## Siehe auch  
 [caller\-Eigenschaft \(Funktion\)](../../javascript/reference/caller-property-function-javascript.md)