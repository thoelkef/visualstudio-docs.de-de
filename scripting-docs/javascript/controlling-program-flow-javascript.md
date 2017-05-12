---
title: "Steuerung des Programmablaufs (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolesche Werte, Programmfluss"
  - "continue-Anweisung"
  - "break-Anweisung"
  - "Ablaufsteuerung, Informationen über die Ablaufsteuerung"
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Steuerung des Programmablaufs (JavaScript)
Normalerweise werden Anweisungen in einem [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Skript nacheinander in der Reihenfolge ausgeführt, in der sie geschrieben werden.  Diese so genannte sequenzielle Ausführung ist die Standardrichtung des Programmablaufs.  
  
 Eine Alternative zur sequenziellen Ausführung ist die Ablaufsteuerung zu einem anderen Teil des Skripts.  Hierbei wird nicht die nächste Anweisung in der Sequenz, sondern stattdessen eine andere Anweisung ausgeführt.  
  
 Damit ein Skript nützlich ist, muss diese Ablaufsteuerung logisch sein.  Die Übertragung der Programmsteuerung ist von einer Entscheidung abhängig, deren Ergebnis eine Wahrheitsaussage ist \(und den booleschen Wert **true** oder **false** zurückgibt\).  Sie erstellen einen Ausdruck und testen dann, ob das Ergebnis "true" lautet.  Es gibt zwei Hauptarten von Programmstrukturen, mit denen Sie dies erreichen können.  
  
 Die erste Struktur ist die Auswahlstruktur.  Sie wird verwendet, um alternative Richtungen des Programmablaufs anzugeben und so eine Abzweigung im Programm zu erstellen \(analog zur Gabelung einer Straße\).  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stehen vier Auswahlstrukturen zur Verfügung:  
  
-   Einzelauswahlstruktur \(**if**\),  
  
-   Zweifachauswahlstruktur \(**if\/else**\),  
  
-   ternärer Inlineoperator `?:` und  
  
-   Mehrfachauswahlstruktur \(`switch`\).  
  
 Der zweite Typ der Programmsteuerstruktur ist die Wiederholungsstruktur.  Verwenden Sie diese, um anzugeben, dass eine Aktion wiederholt werden soll, solange eine Bedingung wahr \(true\) ist.  Wenn die Bedingungen der Steueranweisung erfüllt sind \(i. d. R. nach einer bestimmten Anzahl von Iterationen\), wird die Steuerung an die nächste Anweisung nach der Wiederholungsstruktur übergeben.  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stehen vier Wiederholungsstrukturen zur Verfügung:  
  
-   Testen des Ausdrucks am Anfang der Schleife \(`while`\),  
  
-   Testen des Ausdrucks am Ende der Schleife \(**do\/while**\),  
  
-   Ausführen für jede Eigenschaft eines Objekts \(**for\/in**\) und  
  
-   Durch einen Zähler gesteuerte Wiederholung \(**for**\).  
  
 Sie können recht komplexe Skripts erstellen, indem Sie Auswahl\- und Wiederholungssteuerstrukturen schachteln und stapeln.  
  
 Eine dritte Form des strukturierten Programmablaufs bildet die Ausnahmebehandlung, die in diesem Dokument nicht behandelt wird.  
  
## Verwenden von bedingten Anweisungen  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt die bedingten Anweisungen **if** und [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md).  In **if**\-Anweisungen wird eine Bedingung getestet, und wenn die Bedingung erfüllt ist, wird der zugehörige [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Code ausgeführt.  In der `if...else`\-Anweisung wird ein anderer Code ausgeführt, wenn der Test der Bedingung fehlschlägt.  Die einfachste Form einer **if**\-Anweisung kann in einer Zeile geschrieben werden. Wesentlich häufiger sind jedoch mehrzeilige **if**\- und `if...else`\-Anweisungen.  
  
 Die folgenden Beispiele enthalten Syntaxkonstrukte, die in **if**\-Anweisungen und `if...else`\-Anweisungen verwendet werden können.  Das erste Beispiel veranschaulicht die einfachste Möglichkeit, den Wert einer booleschen Variablen zu überprüfen.  Ausschließlich dann, wenn die Auswertung des Elements in Klammern true ergibt \(oder eine Umwandlung in **true** erfolgen kann\), wird die Anweisung oder der Anweisungsblock hinter **if** ausgeführt.  
  
```javascript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## Bedingter Operator  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt auch eine implizite Form für die Bedingung.  Hierbei wird nach der zu testenden Bedingung ein Fragezeichen \(anstelle des Worts **if** vor der Bedingung\) verwendet.  Zudem werden zwei Alternativen angegeben, eine Alternative für den Fall, dass die Bedingung erfüllt ist, und eine andere Alternative, wenn dies nicht der Fall ist.  Diese Alternativen müssen durch einen Doppelpunkt getrennt werden.  
  
```javascript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Wenn Sie mehrere Bedingungen zusammen überprüfen möchten und davon ausgehen, dass eine dieser Bedingungen mit größerer Wahrscheinlichkeit erfüllt bzw. nicht erfüllt wird als die anderen, können Sie die Ausführung des Skripts mithilfe der so genannten "Kurzschlussauswertung" beschleunigen.  Wenn [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] einen logischen Ausdruck auswertet, werden nur so viele Unterausdrücke ausgewertet, wie zur Erzielung eines Ergebnisses erforderlich sind.  
  
 Beispielsweise wird bei einem AND\-Ausdruck wie \(\(x \=\= 123\) && \(y \=\= 6\)\) in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] zuerst überprüft, ob x gleich 123 ist.  Wenn dies nicht der Fall ist, kann der gesamte Ausdruck selbst dann nicht "true" ergeben, wenn y gleich 6 ist.  Daher wird der Test für y nie durchgeführt, und [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] gibt den Wert **false** zurück.  
  
 Ähnliches gilt, wenn nur eine von mehreren Bedingungen **true** sein muss \(beim Einsatz des Operators &#124;&#124;\). In diesem Fall wird die Überprüfung beendet, sobald eine beliebige Bedingung "true" ergibt.  Dies ist sehr effizient, wenn die zu überprüfenden Bedingungen die Ausführung von Funktionsaufrufen oder andere komplexe Ausdrücke enthalten.  Achten Sie daher beim Schreiben von OR\-Ausdrücken darauf, die Bedingungen, die wahrscheinlich zu **true** ausgewertet werden, an erster Stelle zu platzieren.  Platzieren Sie beim Schreiben von AND\-Ausdrücken die Bedingungen an erster Stelle, die höchstwahrscheinlich **false** ergeben.  
  
 Wenn Sie Skripts auf diese Weise anlegen, hat dies den Vorteil, dass **runsecond\(\)** im folgenden Beispiel nicht ausgeführt wird, wenn **runfirst\(\)** 0 zurückgibt.  
  
```javascript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## Verwenden von Schleifen  
 Es gibt mehrere Möglichkeiten, eine Anweisung oder einen Anweisungsblock wiederholt auszuführen.  Eine wiederholte Ausführung wird als *Schleife* oder *Iteration* bezeichnet.  Eine Iteration ist ein einfacher Durchlauf durch eine Schleife.  Der Vorgang wird i. d. R. durch die Überprüfung einer Variablen gesteuert, deren Wert sich bei jedem Schleifendurchlauf ändert.  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] werden vier Schleifentypen unterstützt: [for](../javascript/reference/for-statement-javascript.md)\-Schleifen, [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)\-Schleifen, [while](../javascript/reference/while-statement-javascript.md)\-Schleifen und [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)\-Schleifen.  
  
## Verwenden von for\-Schleifen  
 Bei der **for**\-Anweisung wird eine Zählervariable, eine Testbedingung und eine Aktion zum Aktualisieren des Zählers angegeben.  Vor jeder Iteration der Schleife wird die Bedingung getestet.  Ist der Test erfolgreich, wird der Code in der Schleife ausgeführt.  Ist der Test nicht erfolgreich, wird der Code in der Schleife nicht ausgeführt, und das Programm wird mit der ersten Codezeile unmittelbar nach der Schleife fortgesetzt.  Nach jeder Ausführung der Schleife wird die Zählervariable aktualisiert, bevor der nächste Schleifendurchlauf beginnt.  
  
 Wenn die Bedingung für die Schleife zu keinem Zeitpunkt erfüllt ist, wird die Schleife nie durchlaufen.  Wenn die Testbedingung stets erfüllt ist, entsteht eine Endlosschleife.  Ersteres kann in einigen Fällen wünschenswert sein. Letzteres ist nur selten beabsichtigt. Achten Sie daher bei der Programmierung der Schleifenbedingung sorgfältig darauf, dass keine Endlosschleife entsteht.  
  
```javascript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## Verwenden von for...in\-Schleifen  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stellt eine spezielle Schleife zum Durchlaufen aller benutzerdefinierten Eigenschaften eines [\-Objekts](../javascript/objects-and-arrays-javascript.md) oder aller Elemente eines Arrays bereit.  Beim Schleifenzähler in einer `for...in`\-Schleife handelt es sich um eine Zeichenfolge, nicht um eine Zahl.  Diese enthält den Namen der aktuellen Eigenschaft oder den Index des aktuellen Arrayelements.  
  
```javascript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Obwohl `for...in`\-Schleifen ähnlich wie die `For Each...Next`\-Schleifen in VBScript aussehen, werden sie nicht die gleiche Weise verarbeitet.  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] durchläuft die **for...in**\-Schleife die Eigenschaften von [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Objekten.  Die VBScript\-Schleife **For Each...Next** durchläuft die Elemente einer Auflistung.  Um Auflistungen in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] in einer Schleife zu durchlaufen, müssen Sie das [Enumeratorobjekt](../javascript/reference/enumerator-object-javascript.md)\-Objekt verwenden oder, sofern vorhanden, die `forEach`\-Methode des Auflistungsobjekts.  Einige Objekte, z. B. Objekte in Internet Explorer, unterstützen zwar sowohl die VBScript\-Schleife **For Each...Next**  als auch die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Schleife **for...in** . Bei den meisten Objekten ist dies jedoch nicht der Fall.  
  
## Verwenden von while\-Schleifen  
 Eine `while`\-Schleife ähnelt einer **for**\-Schleife.  Sie unterscheiden sich dadurch, dass eine `while`\-Schleife nicht über eine integrierte Zählervariable oder einen Aktualisierungsausdruck verfügt.  Sie verwenden eine `while`\-Schleife, wenn eine Anweisung oder ein Anweisungsblock wiederholt ausgeführt werden soll, die Regel zur Schleifensteuerung jedoch komplexer ist als "führe diesen Code n\-mal aus".  Im folgenden Beispiel wird das Internet Explorer\-Objektmodell mit einer `while`\-Schleife verwendet, um dem Benutzer eine einfache Fragen zu stellen.  
  
```javascript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Da `while`\-Schleifen keine explizit integrierten Zählervariablen besitzen, können sie schneller zu Endlosschleifen führen als andere Schleifentypen.  Darüber hinaus kann es leicht passieren, dass Sie eine `while`\-Schleife schreiben, in der die Bedingung tatsächlich nie aktualisiert wird. Dies liegt besonders daran, dass es nicht immer einfach ist, herauszufinden, wo und wann die Schleifenbedingung aktualisiert wird.  Gehen Sie daher beim Erstellen von `while`\-Schleifen sehr sorgfältig vor.  
  
 Wie oben erwähnt, gibt es in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] auch eine **do...while** \-Schleife, die der while\-Schleife ähnelt. Sie unterscheidet sich jedoch darin, dass sie immer mindestens einmal ausgeführt wird, da die Bedingung am Ende der Schleife und nicht an deren Anfang getestet wird.  Beispielsweise kann die obige Schleife wie folgt neu geschrieben werden:  
  
```javascript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## Verwenden von break\- und continue\-Anweisungen  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] wird die [break](../javascript/reference/break-statement-javascript.md) \-Anweisung verwendet, um die Ausführung einer Schleife anzuhalten, wenn eine bestimmte Bedingung erfüllt ist. \(Beachten Sie, dass **break** auch verwendet wird, um einen `switch`\-Block zu beenden.\)  Mit der [continue](../javascript/reference/continue-statement-javascript.md)\-Anweisung können Sie unmittelbar zur nächsten Iteration wechseln und den Rest des Codeblocks überspringen. Dabei wird gleichzeitig die Zählervariable aktualisiert, sofern es sich um eine **for**\-Schleife oder eine `for...in`\-Schleife handelt.  
  
 Das folgende Beispiel baut auf dem vorherigen Beispiel auf. Hier werden die Anweisungen **break** und **continue** verwendet, um die Schleife zu steuern.  
  
```javascript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```