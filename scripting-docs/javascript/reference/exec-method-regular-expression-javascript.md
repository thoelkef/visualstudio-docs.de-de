---
title: "exec-Methode (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec-Methode"
  - "übereinstimmende Zeichenfolgen"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec-Methode (regul&#228;rer Ausdruck) (JavaScript)
Führt eine Suche nach dem Muster eines regulären Ausdrucks in einer Zeichenfolge durch und gibt ein Array mit den Ergebnissen dieser Suche zurück.  
  
## Syntax  
  
```  
  
rgExp.exec(str)   
```  
  
## Parameter  
 `rgExp`  
 Erforderlich.  Eine Instanz eines **Regular Expression**\-Objekts, in der das Muster des regulären Ausdrucks und anwendbare Flags enthalten sind.  
  
 `str`  
 Erforderlich.  Das `String`\-Objekt oder Zeichenfolgenliteral, in dem die Suche ausgeführt werden soll.  
  
## Hinweise  
 Wenn die `exec`\-Methode keine Übereinstimmung findet, gibt sie den Wert `null` zurück.  Wenn sie eine Übereinstimmung findet, gibt `exec` ein Array zurück, und die Eigenschaften des globalen `RegExp`\-Objekts werden aktualisiert, um die Ergebnisse der Übereinstimmung anzuzeigen.  Das Element 0 des Arrays enthält die gesamte Übereinstimmung, während die Elemente 1 bis *n* alle innerhalb der Übereinstimmung aufgetretenen Teilübereinstimmungen enthalten.  Dieses Verhalten entspricht dem Verhalten der `match`\-Methode ohne festgelegtes global\-Flag \(**g**\).  
  
 Wenn das globale Flag für einen regulären Ausdruck festgelegt wird, durchsucht `exec` die Zeichenfolge ab der Position, die durch den Wert von `lastIndex` angegeben wurde.  Wenn das globale Flag nicht festgelegt wird, ignoriert `exec` den Wert von `lastIndex` und durchsucht die Zeichenfolge ab ihrem Anfang.  
  
 Das von der `exec`\-Methode zurückgegebene Array hat drei Eigenschaften: **input**, **index** und **lastIndex**. Die **input**\-Eigenschaft enthält die gesamte durchsuchte Zeichenfolge.  Die **index**\-Eigenschaft enthält die Position der übereinstimmenden untergeordneten Zeichenfolge innerhalb der gesamten durchsuchten Zeichenfolge.  Die `lastIndex`\-Eigenschaft enthält die Position, die auf das letzte Zeichen der Übereinstimmung folgt.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `exec`\-Methode veranschaulicht:  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [match\-Methode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search\-Methode \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test\-Methode \(regulärer Ausdruck\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/de-de/3b62e27c-4f07-4726-a95b-6e841807bfaf)