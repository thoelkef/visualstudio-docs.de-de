---
title: "global-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global-Eigenschaft"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global-Eigenschaft (regul&#228;rer Ausdruck) (JavaScript)
Gibt einen booleschen Wert zurück, der den Zustand des mit einem regulären Ausdruck verwendeten global\-Flags \(**g**\) angibt.  Der Standardwert lautet **false**.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
rgExp.global  
```  
  
## Hinweise  
 Der erforderliche `rgExp`\-Verweis ist eine Instanz eines **Regular Expression**\-Objekts.  
  
 Die `global`\-Eigenschaft gibt **true** zurück, wenn das global\-Flag für einen regulären Ausdruck festgelegt worden ist; andernfalls wird **false** zurückgegeben.  
  
 Falls verwendet, gibt das global\-Flag an, dass bei einer Suche alle Vorkommen des Musters in der zu durchsuchenden Zeichenfolge gesucht werden sollen, und nicht nur das erste.  Dies wird auch "globale Suche" genannt.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `global`\-Eigenschaft veranschaulicht.  Wenn Sie **g** an die unten angezeigte Funktion übergeben, werden alle Vorkommen des Worts "the" durch das Wort "a" ersetzt.  Das "The" am Anfang der Zeichenfolge wird nicht ersetzt, da das **i**\-Flag \(Groß\-\/Kleinschreibung ignorieren\) nicht an die Funktion übergeben wird.  
  
 Diese Funktion zeigt die Bedingung der Eigenschaften an, die den zulässigen Flags für reguläre Ausdrücke zugeordnet sind, wobei es sich um **g**, **i** und **m** handelt.  Die Funktion zeigt auch die Zeichenfolge mit allen vorgenommenen Ersetzungen an.  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## Beispiel  
 Nachfolgend ist die resultierende Ausgabe aufgeführt.  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Siehe auch  
 [ignoreCase\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline\-Eigenschaft \(regulärer Ausdruck\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)