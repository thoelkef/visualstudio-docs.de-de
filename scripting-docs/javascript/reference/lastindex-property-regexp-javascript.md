---
title: "lastIndex-Eigenschaft (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex-Eigenschaft"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex-Eigenschaft (RegExp) (JavaScript)
Gibt die Zeichenposition zurück, die auf die nächste Übereinstimmung in einer durchsuchten Zeichenfolge folgt.  
  
## Syntax  
  
```  
  
RegExp.lastIndex  
```  
  
## Hinweise  
 Das mit dieser Eigenschaft verknüpfte Objekt ist immer das globale `RegExp`\-Objekt.  
  
 Die `lastIndex`\-Eigenschaft ist nullbasiert, d. h., der Index des ersten Zeichens ist gleich Null.  Der Anfangswert ist \-1.  Der Wert wird geändert, wenn eine Übereinstimmung gefunden wurde.  
  
 Die `lastIndex`\-Eigenschaft wird von den Methoden `exec` und **test** des `RegExp`\-Objekts und den Methoden `match`, **replace** und **split** des `String`\-Objekts geändert.  
  
 Für die Werte von `lastIndex` gelten die folgenden Regeln:  
  
-   Gibt es keine Entsprechung, wird `lastIndex` auf \-1 gesetzt.  
  
-   Ist `lastIndex` größer als die Länge der Zeichenfolge, schlagen **test** und `exec` fehl, und `lastIndex` wird auf \-1 gesetzt.  
  
-   Ist `lastIndex` gleich der Länge der Zeichenfolge, so gibt es eine Entsprechung für den regulären Ausdruck, wenn das Muster der leeren Zeichenfolge entspricht.  Andernfalls schlägt die Entsprechung fehl, und `lastIndex` wird auf \-1 zurückgesetzt.  
  
-   Ansonsten wird für `lastIndex` die nächste Position festgelegt, die auf die letzte Entsprechung folgt.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `lastIndex`\-Eigenschaft veranschaulicht.  Diese Funktion durchläuft eine Suchzeichenfolge und gibt die Werte **index** und `lastIndex` für jedes Wort in der Zeichenfolge aus.  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## Siehe auch  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)