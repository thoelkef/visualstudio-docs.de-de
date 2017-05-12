---
title: "test-Methode (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Testmethode"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test-Methode (regul&#228;rer Ausdruck) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Muster in einer durchsuchten Zeichenfolge vorhanden ist.  
  
## Syntax  
  
```  
  
rgExp.test(str)   
```  
  
## Parameter  
 `rgExp`  
 Erforderlich.  Eine Instanz eines **Regular Expression**\-Objekts, die das Muster des regulären Ausdrucks sowie anwendbare Flags enthält.  
  
 `str`  
 Erforderlich.  Die zu durchsuchende Zeichenfolge.  
  
## Hinweise  
 Die **test**\-Methode prüft, ob ein Muster in einer Zeichenfolge vorhanden ist und gibt **true** zurück, falls dies zutrifft. Andernfalls wird **false** zurückgegeben.  
  
 Die Eigenschaften des globalen `RegExp`\-Objekts werden von der **test**\-Methode nicht geändert.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **test**\-Methode.  Übergeben Sie der Funktion das Muster eines regulären Ausdrucks und eine Zeichenfolge, um dieses Beispiel zu verwenden.  Die Funktion testet, ob das Muster des regulären Ausdrucks in der Zeichenfolge vorkommt, und gibt eine Zeichenfolge zurück, die die Ergebnisse dieser Suche anzeigt:  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)