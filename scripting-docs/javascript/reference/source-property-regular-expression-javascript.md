---
title: "source-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "source"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Source-Eigenschaft"
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# source-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript)
Gibt eine Kopie des Textes mit dem Muster eines regulären Ausdrucks zurück.  Schreibgeschützt.  Das `rgExp`\-Argument ist ein **Regular expression**\-Objekt.  Es kann ein Variablenname oder ein Literal sein.  
  
## Syntax  
  
```  
  
rgExp.source  
```  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **source**\-Eigenschaft:  
  
```javascript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)