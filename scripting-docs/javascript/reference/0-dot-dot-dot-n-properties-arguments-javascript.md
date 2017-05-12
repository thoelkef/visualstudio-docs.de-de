---
title: "0...n-Eigenschaften (Argumente) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "0...n-Eigenschaften"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n-Eigenschaften (Argumente) (JavaScript)
Gibt den tatsächlichen Wert einzelner Argumente aus einem **arguments**\-Objekt zurück, das von der **arguments**\-Eigenschaft einer ausgeführten Funktion zurückgegeben wird.  
  
## Syntax  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## Parameter  
 *function*  
 Optional.  Der Name des aktuell ausgeführten `Function`\-Objekts.  
  
 0, 1, 2, *, n*  
 Erforderlich.  Nicht negative ganze Zahl im Bereich von 0 bis *n*, wobei 0 das erste Argument und *n* das letzte Argument darstellt.  Der Wert des letzten Arguments *n* ist **arguments.length\-1**.  
  
## Hinweise  
 Die von 0 zurückgegebenen Werte.  .  .  Der ausgeführten Funktion werden n Eigenschaften als eigentliche Werte übergeben.  Obwohl es sich eigentlich nicht um ein Array von Argumenten handelt, wird auf die einzelnen Argumente, aus denen das **arguments**\-Objekt besteht, auf die gleiche Weise zugegriffen wie auf Arrayelemente.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung von **0 . . .**  ***n***\-Eigenschaften des **arguments**\-Objekts.  Um das Beispiel besser zu verstehen, übergeben Sie der Funktion eines oder mehrere Argumente:  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [arguments\-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Function\-Objekt](../../javascript/reference/function-object-javascript.md)  
  
## Siehe auch  
 [length\-Eigenschaft \(Arguments\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length\-Eigenschaft \(Funktion\)](../../javascript/reference/length-property-function-javascript.md)