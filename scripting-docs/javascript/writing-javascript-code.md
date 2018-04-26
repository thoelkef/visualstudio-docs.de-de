---
title: Schreiben von JavaScript-Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>Schreiben von JavaScript-Code
Wie jede andere Programmiersprache auch ist [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] in Anweisungen, Blocks, die aus verschiedenen miteinander verknüpften Anweisungen bestehen, und Kommentare unterteilt. In einer Anweisung können Sie Variablen, Zeichenfolgen, Nummern und Ausdrücke verwenden.  
  
## <a name="statements"></a>Anweisungen  
 Ein [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Programm ist eine Auflistung von Anweisungen. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Anweisungen kombinieren Ausdrücke so miteinander, dass sie eine vollständige Aufgabe ausführen können.  
  
 Eine Anweisung besteht aus mindestens einem Ausdruck, Schlüsselwort oder Operator (Symbole). In der Regel werden Anweisungen in nur eine Zeile geschrieben, obwohl sie auch länger sein können. Zudem können auch mehrere Anweisungen in dieselbe Zeile geschrieben werden, wenn man sie durch Semikolons voneinander abtrennt. Für gewöhnlich beginnt jede neue Zeile mit einer neuen Anweisung. Sie sollten Ihre Anweisungen explizit beenden. Dies funktioniert mithilfe eines Semikolons („;“). Dieses Zeichen gilt als Abschlusszeichen für [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Anweisungen.  
  
 Im Folgenden werden zwei Beispiele für [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Anweisungen genannt. Die Sätze nach den //-Zeichen sind *Kommentare*, d.h. erläuternde Hinweise in dem Programm.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Eine Gruppe von [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Anweisungen, die von geschweiften Klammern ({}) eingeschlossen wird, wird als *Block* bezeichnet. Anweisungen, die in einen Block gruppiert werden, können in der Regel als eine Anweisung behandelt werden. Das bedeutet, dass Sie an den meisten Stellen, an denen [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] nur eine Anweisung erwartet, einen Block verwenden können. Die Header von **For**- und `while`-Schleifen stellen eine wichtige Ausnahme dar. Beachten Sie, dass zwar einzelne Anweisungen in einem Block mit Semikolons enden, der Block an sich jedoch nicht.  
  
 Blöcke werden in der Regel in Funktionen und Bedingungen verwendet. Beachten Sie, dass [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] im Gegensatz zu C++ und anderen Sprachen einen Block nicht als neuen Bereich anerkennt. Nur Funktionen können einen neuen Bereich erstellen.  
  
 Im folgenden Beispiel enthält die `else`-Klausel einen Block mit zwei Anweisungen, der von geschweiften Klammern umgeben ist. Der Block wird als eine einzige Anweisung behandelt. Außerdem besteht die Funktion aus einem Block mit Anweisungen, der von geschweiften Klammern umgeben ist. Die Anweisungen unter der Funktion gehören nicht zu dem Block. Aus diesem Grund sind sie auch kein Bestandteil der Funktionsdefinition.  
  
```JavaScript  
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
  
## <a name="comments"></a>Kommentare  
 Ein einzeiliger [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Kommentar beginnt mit zwei Schrägstrichen („//“). Im Folgenden wird ein Beispiel mit einem einzeiligen Kommentar dargestellt.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Ein mehrzeiliger [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Kommentar beginnt mit einem Schrägstrich und einem Sternchen (/\*) und endet mit den gleichen Zeichen in der umgekehrten Reihenfolge („\*/“).  
  
```JavaScript  
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
>  Wenn Sie versuchen, einen mehrzeiligen Kommentar in einen anderen einzubetten, interpretiert [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] den daraus entstandenen mehrzeiligen Kommentar auf nicht erwartete Weise. Die Zeichenfolge „*/“, die das Ende des eingebetteten mehrzeiligen Kommentars darstellt, wird als Ende des gesamten mehrzeiligen Kommentars interpretiert. Das bedeutet, dass der Text, der dem eingebetteten mehrzeiligen Kommentar folgt, nicht auskommentiert wird. Stattdessen wird er als [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Code interpretiert, und generiert Syntaxfehler.  
  
 Es wird empfohlen, alle Kommentare als Blöcke mit einzeiligen Kommentaren zu schreiben. So können größere Codesegmente später mit einem mehrzeiligen Kommentar auskommentiert werden.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Zuweisungen und Gleichheit  
 Das Gleichheitszeichen („=“) wird in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Anweisungen verwendet, um Variablen Werte zuzuweisen. Daher gilt es als Zuweisungsoperator. Der linke Operand des =-Operators ist immer ein Lvalue. Beispiele für Lvalues:  
  
-   Variablen  
  
-   Arrayelemente  
  
-   Objekteigenschaften  
  
 Der rechte Operand des =-Operators ist immer der R-Wert. R-Werte können beliebige Werte beliebiger Typen sein, einschließlich des Werts eines Ausdrucks. Im Folgenden wird eine [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Zuweisungsanweisung dargestellt.  
  
```JavaScript  
var anInteger = 3;  
```  
  
 Der [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Compiler interpretiert diese Anweisung wie folgt: „Wert 3 der **anInteger**-Variable zuordnen“ oder „**anInteger** nimmt den Wert 3 an“.  
  
 Stellen Sie sicher, dass Ihnen der Unterschied zwischen dem =-Operator (Zuweisung) und dem ==-Operator (Gleichheit) deutlich ist. Wenn Sie zwei Werte miteinander vergleichen wollen, um herauszufinden, ob sie gleich sind, verwenden Sie zwei Gleichheitszeichen („==“). Dieser Vorgang wird detailliert unter [Steuerung des Programmablaufs](../javascript/controlling-program-flow-javascript.md) erläutert.  
  
## <a name="expressions"></a>Ausdrücke  
 Jeder gültige [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Typ (eine Nummer, eine Zeichenfolge, ein Objekt, etc.) kann ein [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Ausdruckswert sein. Literale sind die einfachsten Ausdrücke. Im Folgenden werden Beispiele für literale [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Ausdrücke dargestellt.  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Kompliziertere Ausdrücke können Variablen, Funktionsaufrufe und andere Ausdrücke enthalten. Sie können Ausdrücke mithilfe von Operatoren miteinander kombinieren, um komplexe Ausdrücke zu erstellen. Operatoren sind z.B. `+` (Addition), `-` (Subtraktion), `*` (Multiplikation) und `/` (Division).  
  
 Im Folgenden sind einige Beispiele für komplexe [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Ausdrücke dargestellt.  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```