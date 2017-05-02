---
title: "ignoreCase-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase-Eigenschaft"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript)
Gibt einen booleschen Wert zurück, der den Zustand des mit einem regulären Ausdruck verwendeten ignoreCase\-Flags \(**i**\) angibt.  Der Standardwert lautet **false**.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
rgExp.ignoreCase  
```  
  
## Hinweise  
 Der erforderliche `rgExp`\-Verweis ist eine Instanz des `RegExp`\-Objekts.  
  
 Die **ignoreCase**\-Eigenschaft gibt **true** zurück wenn das ignoreCase\-Flag für einen regulären Ausdruck festgelegt ist; andernfalls wird **false** zurückgegeben.  
  
 Falls verwendet, gibt das ignoreCase\-Flag an, dass die Groß\-\/Kleinschreibung bei einer Suche nach dem Muster in der zu durchsuchenden Zeichenfolge nicht beachtet werden sollte.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ignoreCase**\-Eigenschaft.  Wenn Sie "gi" an die unten angezeigte Funktion übergeben, werden alle Vorkommen des Worts "the" durch das Wort "a" ersetzt, einschließlich des ersten "The".  Der Grund dafür liegt darin, dass bei festgelegtem ignoreCase\-Flag die Groß\- und Kleinschreibung bei der Suche ignoriert wird.  Deshalb wird beim Vergleich nicht zwischen "T" und "t" unterschieden.  
  
 Diese Funktion gibt die booleschen Werte zurück, die den Zustand der zulässigen Flags für reguläre Ausdrücke angeben: **g**, **i** und **m**.  Die Funktion gibt auch die Zeichenfolge mit allen vorgenommenen Ersetzungen zurück.  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## Beispiel  
 Nachfolgend ist die resultierende Ausgabe aufgeführt.  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [global\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)