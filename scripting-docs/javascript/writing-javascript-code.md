---
title: "Schreiben von JavaScript-Code | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Code, JavaScript-Syntax"
  - "Kommentare, JavaScript-Code"
  - "JavaScript-Code"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Schreiben von JavaScript-Code
Wie viele andere Programmiersprachen ist [!INCLUDE[javascript](../includes/javascript-md.md)] in Anweisungen, Blöcke, die aus verknüpften Sätzen von Anweisungen bestehen, und Kommentare gegliedert.  Innerhalb einer Anweisung können Sie Variablen, Zeichenfolgen, Zahlen und Ausdrücke verwenden.  
  
## Anweisungen  
 Ein [!INCLUDE[javascript](../includes/javascript-md.md)]\-Programm ist eine Auflistung von Anweisungen.  [!INCLUDE[javascript](../includes/javascript-md.md)]\-Anweisungen kombinieren Ausdrücke so, dass eine vollständige Aufgabe ausgeführt wird.  
  
 Eine Anweisung besteht aus einem oder mehreren Ausdrücken, Schlüsselwörtern oder Operatoren \(Symbolen\).  In der Regel wird eine Anweisung in eine einzelne Zeile geschrieben, sie kann sich jedoch auch über zwei oder mehr Zeilen erstrecken.  Außerdem ist es möglich, in eine Zeile zwei oder mehr Anweisungen zu schreiben. Dazu werden sie durch Semikolons getrennt.  Im Allgemeinen beginnt mit jeder neuen Zeile eine neue Anweisung.  Es empfiehlt sich, die Anweisungen explizit zu beenden.  Dies geschieht mit dem Semikolon \(;\), dem [!INCLUDE[javascript](../includes/javascript-md.md)]\-Endezeichen für Anweisungen.  
  
 Im Folgenden finden Sie zwei Beispiele für [!INCLUDE[javascript](../includes/javascript-md.md)]\-Anweisungen.  Die Sätze nach den \/\/\-Zeichen sind *Kommentare*, die erläuternde Hinweise im Programm sind.  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Eine von geschweiften Klammern \({}\) eingeschlossene Gruppe von [!INCLUDE[javascript](../includes/javascript-md.md)]\-Anweisungen wird als *Block* bezeichnet.  In einem Block gruppierte Anweisungen können im Allgemeinen als eine einzige Anweisung behandelt werden.  Das bedeutet, dass Sie Blöcke an den meisten Stellen verwenden können, an denen [!INCLUDE[javascript](../includes/javascript-md.md)] eine einzelne Anweisung erwartet.  Zu den wichtigen Ausnahmen gehören die Header von **for**\-Schleifen und `while`\-Schleifen.  Beachten Sie, dass die einzelnen Anweisungen innerhalb eines Blocks mit einem Semikolon beendet werden, der Block selbst jedoch nicht.  
  
 Blöcke werden im Allgemeinen in Funktionen und Bedingungen verwendet.  Beachten Sie, dass in [!INCLUDE[javascript](../includes/javascript-md.md)] ein Block im Unterschied zu C\+\+ und einigen anderen Sprachen nicht als neuer Bereich gilt; nur Funktionen erstellen einen neuen Gültigkeitsbereich.  
  
 Im folgenden Beispiel enthält die `else`\-Klausel einen Block aus zwei Anweisungen, die von geschweiften Klammern eingeschlossen sind.  Der Block wird als einzelne Anweisung behandelt.  Auch die Funktion selbst besteht aus einem Block von Anweisungen, die von geschweiften Klammern eingeschlossen sind.  Die Anweisungen unterhalb der Funktion liegen außerhalb des Blocks und können daher nicht Bestandteil der Funktionsdefinition sein.  
  
```javascript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## Kommentare  
 Ein einzeiliger [!INCLUDE[javascript](../includes/javascript-md.md)]\-Kommentar beginnt mit zwei Schrägstrichen \(\/\/\).  Hier folgt ein Beispiel für einen einzeiligen Kommentar.  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Ein mehrzeiliger [!INCLUDE[javascript](../includes/javascript-md.md)]\-Kommentar beginnt mit einem Schrägstrich und einem Sternchen \(\/\*\) und endet mit der umgekehrten Kombination \(\*\/\).  
  
```javascript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Wenn Sie versuchen, einen mehrzeiligen Kommentar in einen anderen einzubetten, interpretiert [!INCLUDE[javascript](../includes/javascript-md.md)] den daraus resultierenden mehrzeiligen Kommentar nicht wie erwartet.  Die Kombination aus Sternchen und Schrägstrich \(\*\/\), die das Ende des eingebetteten mehrzeiligen Kommentars markiert, wird als das Ende des gesamten mehrzeiligen Kommentars interpretiert.  Dies bedeutet, dass der Text, der dem eingebetteten mehrzeiligen Kommentar folgt, nicht auskommentiert wird; stattdessen wird er als [!INCLUDE[javascript](../includes/javascript-md.md)] Code interpretiert, und es werden Syntaxfehler generiert.  
  
 Es wird empfohlen, alle Kommentare als Blöcke aus einzeiligen Kommentaren zu schreiben.  Auf diese Weise können Sie später große Codesegmente durch einen mehrzeiligen Kommentar auskommentieren.  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## Zuweisungen und Gleichheit  
 Das Gleichheitszeichen \(\=\) dient in [!INCLUDE[javascript](../includes/javascript-md.md)]\-Anweisungen dazu, Werte Variablen zuzuweisen: Es ist der Zuweisungsoperator.  Der linke Operand des Operators \= ist stets ein Lvalue.  Beispiele für Lvalues sind:  
  
-   Variablen,  
  
-   Arrayelemente,  
  
-   Objekteigenschaften.  
  
 Der rechte Operand des Operators \= ist stets ein Rvalue.  Rvalues können ein willkürlicher Wert eines beliebigen Typs sein, beispielsweise der Wert eines Ausdrucks.  Hier folgt ein Beispiel für eine [!INCLUDE[javascript](../includes/javascript-md.md)]\-Zuweisungsanweisung.  
  
```javascript  
var anInteger = 3;  
```  
  
 Der [!INCLUDE[javascript](../includes/javascript-md.md)]\-Compiler interpretiert diese Anweisung wie folgt: "Der Variablen **anInteger** den Wert 3 zuweisen" oder "**anInteger** nimmt den Wert 3 an".  
  
 Es ist sehr wichtig, dass Ihnen die Unterschiede zwischen dem Operator \= \(Zuweisung\) und dem Operator \=\= \(Gleichheit\) klar sind.  Wenn Sie zwei Werte vergleichen möchten, um festzustellen, ob sie gleich sind, verwenden Sie zwei Gleichheitszeichen \(\=\=\).  Dies wird unter [Steuern des Programmablaufs](../javascript/controlling-program-flow-javascript.md) ausführlich erläutert.  
  
## Ausdrücke  
 Ein [!INCLUDE[javascript](../includes/javascript-md.md)]\-Ausdruckswert kann jeden beliebigen gültigen [!INCLUDE[javascript](../includes/javascript-md.md)]\-Typ haben: eine Zahl, eine Zeichenfolge, ein Objekt usw.  Die einfachsten Ausdrücke sind Literale.  Hier sind einige Beispiele für [!INCLUDE[javascript](../includes/javascript-md.md)]\-Literalausdrücke.  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Kompliziertere Ausdrücke können Variablen, Funktionsaufrufe und andere Ausdrücke enthalten.  Mithilfe von Operatoren können Sie Ausdrücke kombinieren und komplexe Ausdrücke erstellen.  Beispiele für Operatoren sind: `+` \(Addition\), `-` \(Subtraktion\), `*` \(Multiplikation\) und `/` \(Division\).  
  
 Hier sind einige Beispiele für komplexe [!INCLUDE[javascript](../includes/javascript-md.md)]\-Ausdrücke.  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```