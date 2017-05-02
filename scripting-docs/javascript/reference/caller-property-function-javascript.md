---
title: "caller-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller-Eigenschaft"
  - "Funktionsaufrufe, Derzeit ausgeführte Funktionen"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller-Eigenschaft (Funktion) (JavaScript)
Ruft die Funktion ab, welche die aktuelle Funktion aufgerufen hat.  
  
## Syntax  
  
```  
  
functionName.caller  
```  
  
## Hinweise  
 Das `functionName`\-Objekt ist der Name einer beliebigen ausgeführten Funktion.  
  
 Die `caller`\-Eigenschaft einer Funktion ist nur während ihrer Ausführung definiert.  Wenn die Funktion auf der obersten Ebene eines [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Programms aufgerufen wird, enthält `caller` den Wert `null`.  
  
 Wird die `caller`\-Eigenschaft in einer Zeichenfolge verwendet, entspricht dies `functionName`.`toString`, d. h., der dekompilierte Text der Funktion wird angezeigt.  
  
 Im folgenden Beispiel wird die Verwendung der `caller`\-Eigenschaft veranschaulicht:  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
## Siehe auch  
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)