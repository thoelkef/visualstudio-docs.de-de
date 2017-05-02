---
title: "multiline-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline-Eigenschaft"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript)
Gibt einen booleschen Wert zurück, der den Zustand des mit einem regulären Ausdruck verwendeten multiline\-Flags \(**m**\) angibt.  Der Standardwert lautet **false**.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
rgExp.multiline  
```  
  
## Hinweise  
 Das erforderliche `rgExp`\-Argument ist eine Instanz des `RegExp`\-Objekts.  
  
 Die **multiline**\-Eigenschaft gibt **true** zurück wenn das multiline\-Flag für einen regulären Ausdruck festgelegt ist; andernfalls wird **false** zurückgegeben.  Die **multiline**\-Eigenschaft ist **true**, wenn das Objekt des regulären Ausdrucks mit dem **m**\-Flag erstellt wurde.  
  
 Wenn **multiline** den Wert **false** hat, stimmt "^" mit der Position am Anfang einer Zeichenfolge und "$" mit der Position am Ende einer Zeichenfolge überein.  Wenn **multiline** den Wert **true** hat, stimmt "^" sowohl mit der Position am Anfang einer Zeichenfolge als auch mit der Position nach einem "\\n" oder "\\r" überein, und "$" stimmt sowohl mit der Position am Ende einer Zeichenfolge als auch mit der Position vor einem "\\n" oder "\\r" überein.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht das Verhalten der **multiline**\-Eigenschaft.  Wenn Sie "m" an die unten dargestellte Funktion übergeben, wird das Wort "while" durch das Wort "and" ersetzt.  Das liegt daran, dass das multiline\-Flag festgelegt ist und das Wort "while" am Anfang der Zeile nach einem Zeilenumbruchzeichen steht.  Das multiline\-Flag ermöglicht die Suche in mehrzeiligen Zeichenfolgen.  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [global\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)