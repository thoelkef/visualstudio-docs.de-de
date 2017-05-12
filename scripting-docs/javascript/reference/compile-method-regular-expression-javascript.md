---
title: "compile-Methode (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile-Methode"
  - "Kompilieren von Quellcode, Reguläre Ausdrücke"
  - "Reguläre Ausdrücke, Kompilieren"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile-Methode (regul&#228;rer Ausdruck) (JavaScript)
Kompiliert einen regulären Ausdruck zur schnelleren Ausführung in ein internes Format.  
  
## Syntax  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## Parameter  
 `rgExp`  
 Erforderlich.  Eine Instanz eines **Regular Expression**\-Objekts.  Kann ein Variablenname oder ein Literal sein.  
  
 *pattern*  
 Erforderlich.  Ein Zeichenfolgenausdruck, der ein zu kompilierendes Muster eines regulären Ausdrucks enthält.  
  
 `flags`  
 Optional.  Folgende verfügbare Flags können kombiniert werden:  
  
-   g \(globale Suche nach allen Vorkommen von *pattern*\)  
  
-   i \(Groß\-\/Kleinschreibung ignorieren\)  
  
-   m \(mehrzeilige Suche\)  
  
## Hinweise  
 Die **compile**\-Methode konvertiert *pattern* zur schnelleren Ausführung in ein internes Format.  Dadurch können beispielsweise reguläre Ausdrücke in Schleifen effizienter verwendet werden.  Ein kompilierter regulärer Ausdruck wirkt beschleunigend, wenn derselbe Ausdruck mehrmals verwendet wird.  Wenn sich der reguläre Ausdruck ändert, entsteht kein Vorteil.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **compile**\-Methode:  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)