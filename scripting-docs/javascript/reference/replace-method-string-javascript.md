---
title: "replace-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace-Methode"
  - "Ersetzen von Zeichenfolgen"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# replace-Methode (String) (JavaScript)
Ersetzt Text in einer Zeichenfolge unter Verwendung eines regulären Ausdrucks oder einer Suchzeichenfolge.  
  
## Syntax  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## Parameter  
 `stringObj`  
 Erforderlich.  Das `String`\-Objekt oder \-Zeichenfolgenliteral, in dem die Ersetzung ausgeführt werden soll.  Diese Zeichenfolge wird nicht von der **replace**\-Methode geändert.  Stattdessen ist der Rückgabewert dieser Methode die Zeichenfolge, die durch die Ersetzung erzeugt wird.  
  
 `rgExp`  
 Erforderlich.  Eine Instanz eines **Regular Expression**\-Objekts, die das Muster des regulären Ausdrucks sowie anwendbare Flags enthält.  Kann auch ein `String`\-Objekt oder \-Zeichenfolgenliteral sein, das den regulären Ausdruck darstellt.  Wenn `rgExp` keine Instanz eines **Regular Expression**\-Objekts ist, wird es in eine Zeichenfolge konvertiert, und es wird eine exakte Suche nach den Ergebnissen durchgeführt. Es wird kein Versuch unternommen, die Zeichenfolge in einen regulären Ausdruck zu konvertieren.  
  
 `replaceText`  
 Erforderlich.  Ein `String`\-Objekt oder \-Zeichenfolgenliteral, das den Text enthält, der jede Übereinstimmung von `rgExp` in `stringObj` ersetzen soll.  In [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher kann das `replaceText`\-Argument auch eine Funktion sein, die den Ersetzungstext zurückgibt.  
  
## Rückgabewert  
 Das Ergebnis der **replace**\-Methode ist eine Kopie von `stringObj`, nachdem die angegebenen Ersetzungen durchgeführt wurden.  
  
## Hinweise  
 Jede der folgenden Übereinstimmungsvariablen kann zum Identifizieren der aktuellsten Übereinstimmung und der Zeichenfolge, aus der sie resultierte, verwendet werden.  Die Übereinstimmungsvariablen können bei Textersetzungen verwendet werden, bei denen die Ersetzungszeichenfolge dynamisch bestimmt werden muss.  
  
|Zeichen|Bedeutung|  
|-------------|---------------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
|**$&**|Gibt diesen Teil von `stringObj` an, der mit dem gesamten Muster übereinstimmt.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
|`$``|Gibt den Teil von `stringObj` an, der der durch **$&** beschriebenen Übereinstimmung vorangestellt wird.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
|`$'`|Gibt den Teil von `stringObj` an, der der durch **$&** beschriebenen Übereinstimmung folgt.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
|`$`  ***n***|Die *n*\-te erfasste Teilübereinstimmung, wobei *n* eine einfache Dezimalzahl zwischen 1 und 9 ist.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
|`$`  ***nn***|Die *nn*\-te erfasste Teilübereinstimmung, wobei *nn* eine zweistellige Dezimalzahl zwischen 01 und 99 ist.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher\)|  
  
 Wenn `replaceText` eine Funktion ist, wird die Funktion für jede übereinstimmende untergeordnete Zeichenfolge mit den Argumenten *m* \+ 3 aufgerufen, wobei *m* der Anzahl von links schließenden Klammern in `rgExp` entspricht.  Das erste Argument ist die übereinstimmende untergeordnete Zeichenfolge.  Die nächsten *m*\-Argumente sind alle Erfassungen, die aus der Suche resultieren.  Das Argument *m* \+ 2 ist der Offset in `stringObj`, an dem die Übereinstimmung auftrat, und das Argument *m* \+ 3 ist `stringObj`.  Das Ergebnis ist eine Zeichenfolge, die daraus resultiert, dass jede übereinstimmende untergeordnete Zeichenfolge durch den entsprechenden Rückgabewert des Funktionsaufrufs ersetzt wird.  
  
 Die **replace**\-Methode aktualisiert die Eigenschaften des globalen `RegExp`\-Objekts.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der **replace**\-Methode zum Ersetzen aller Instanzen von „the“ durch „a“ veranschaulicht.  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Darüber hinaus können durch die **replace**\-Methode Teilausdrücke im Muster ersetzt werden.  Im folgenden Beispiel wird jedes Paar von Wörtern in der Zeichenfolge ausgetauscht.  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 Im folgenden Beispiel, das in [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] und höher ausgeführt werden kann, wird die Verwendung einer Funktion gezeigt, die den Ersatztext zurückgibt.  Sie ersetzt jede Instanz einer Zahl, auf die „F“ folgt, durch eine Celsiuskonvertierung.  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [exec\-Methode \(regulärer Ausdruck\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match\-Methode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [search\-Methode \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test\-Methode \(regulärer Ausdruck\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/de-de/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/de-de/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/de-de/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [Beispielapp für HTML5\-Drag & Drop](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)