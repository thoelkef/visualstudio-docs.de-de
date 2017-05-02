---
title: "HTML-Tag-Methode (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Anchormethode [JavaScript]"
  - "big-Methode [JavaScript]"
  - "blink-Methode [JavaScript]"
  - "bold-Methode [JavaScript]"
  - "fixed-Methode [JavaScript]"
  - "fontcolor-Methode [JavaScript]"
  - "fontsize-Methode [JavaScript]"
  - "HTML-Tag-Methode [JavaScript]"
  - "italics-Methode [JavaScript]"
  - "link-Methode [JavaScript]"
  - "small-Methode [JavaScript]"
  - "sub-Methode [JavaScript]"
  - "sup-Methode [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# HTML-Tag-Methode (JavaScript)
Sie können HTML\-Tag\-Methoden verwenden, um in einem `String`\-Objekt HTML\-Elemente um Text herum zu platzieren.  
  
## Syntax  
 Die folgende Tabelle enthält die Syntax und eine Beschreibung der einzelnen HTML\-Tag\-Methoden.  
  
 In der Syntaxspalte ist `string1` ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 Die Standardspalte enthält Empfehlungen des [World Wide Web Consortium \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) für HTML 4.  "Abzuraten" gibt an, dass statt des HTML\-Elements besser Stylesheets verwendet werden sollten.  
  
|Syntax|Methodenbeschreibung|Parameterbeschreibung|Standard|  
|------------|--------------------------|---------------------------|--------------|  
|`string1`.anchor\(`name`\)|Fügt ein HTML\-Tag anchor mit einem NAME\-Attribut vor und nach dem Text ein.|Der `name`\-Parameter ist der Text, der in das NAME\-Attribut des HTML\-Tags anchor eingefügt werden soll.||  
|`string1`.big \(\)|Fügt die HTML\-Tags \<BIG\> vor und nach dem Text ein.||Abzuraten|  
|`string1`.blink \(\)|Fügt die HTML\-Tags \<BLINK\> vor und nach dem Text ein.  Das \<BLINK\>\-Tag wird in Internet Explorer nicht unterstützt.||Nicht im Standard|  
|`string1`.bold\(\)|Fügt die HTML\-Tags \<B\> vor und nach dem Text ein.||Abzuraten|  
|`string1`.fixed\(\)|Fügt die HTML\-Tags \<TT\> vor und nach dem Text ein.||Abzuraten|  
|`string1`.fontcolor \(`color`\)|Fügt die HTML\-Tags \<FONT\> mit einem COLOR\-Attribut vor und nach dem Text ein.|Der `color`\-Parameter ist ein Zeichenfolgenwert, der den Hexadezimalwert oder den vordefinierten Namen einer Farbe enthält.  Die gültigen vordefinierten Farbnamen hängen vom [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Hostbrowser und dessen Version ab.|Veraltet|  
|`string1`.fontsize\(`size`\)|Fügt die HTML\-Tags \<FONT\> mit einem SIZE\-Attribut vor und nach dem Text ein.|Der `size`\-Parameter ist ein ganzzahliger Wert, der die Größe des Texts angibt.  Die gültigen ganzzahligen Werte hängen vom [!INCLUDE[javascript](../../includes/javascript-md.md)] Hostbrowser und deren Version ab.|Veraltet|  
|`string1`.italics\(\)|Fügt die HTML\-Tags \<I\> vor und nach dem Text ein.||Abzuraten|  
|`string1`.link\(`href`\)|Platziert ein HTML\-Tag anchor mit einem HREF\-Attribut vor und nach dem Text.|Der `href`\-Parameter ist der Text, der in das HREF\-Attribut des HTML\-Tags anchor eingefügt werden soll.||  
|`string1`.small\(\)|Fügt die HTML\-Tags \<SMALL\> vor und nach dem Text ein.||Abzuraten|  
|`string1`.strike\(\)|Fügt die HTML\-Tags \<STRIKE\> vor und nach dem Text ein.||Veraltet|  
|`string1`.sub\(\)|Fügt die HTML\-Tags \<SUB\> vor und nach dem Text ein.|||  
|`string1`.sup \(\)|Fügt die HTML\-Tags \<SUP\> vor und nach dem Text ein.|||  
  
## Hinweise  
 Es wird nicht überprüft, ob die HTML\-Tags bereits auf die Zeichenfolge angewendet wurden.  
  
## Beispiel  
 Die folgenden Beispiele veranschaulichen die Verwendung dieser HTML\-Tag\-Methoden.  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)