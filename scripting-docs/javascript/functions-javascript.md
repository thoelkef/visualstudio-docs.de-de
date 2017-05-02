---
title: "Funktionen (JavaScript) | Microsoft Docs"
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
  - "systeminterne JavaScript-Funktionen"
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Funktionen (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Funktionen führen Aktionen aus; sie können auch Werte zurückgeben.  Manchmal handelt es sich dabei um Ergebnisse von Berechnungen oder Vergleichen.  Funktionen werden auch als „globale Methoden“ bezeichnet.  
  
 Funktionen vereinen mehrere Vorgänge unter einem einzigen Namen.  Auf diese Weise können Sie den Code optimieren.  Sie können einen Satz Anweisungen schreiben, ihn benennen und dann den gesamten Anweisungssatz ausführen, indem Sie ihn aufrufen und alle erforderlichen Daten an ihn übergeben.  
  
 Sie übergeben Informationen an eine Funktion, indem Sie die Informationen nach dem Namen der Funktion in Klammern einschließen.  An eine Funktion übergebene Informationen werden als Argumente oder Parameter bezeichnet.  Manche Funktionen akzeptieren überhaupt keine Argumente, während andere ein oder mehrere Argumente verwenden können.  Bei einigen Funktionen hängt die Anzahl der Argumente davon ab, wie Sie die Funktion verwenden.  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt zwei Arten von Funktionen: in die Sprache integrierte und vom Benutzer erstellte Funktionen.  
  
## Integrierte Funktionen  
 Die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Sprache enthält mehrere integrierte Funktionen.  Mit einigen dieser Funktionen können Sie Ausdrücke und Sonderzeichen verarbeiten, während andere Zeichenfolgen in numerische Werte konvertieren.  
  
 Informationen zu diesen integrierten Funktionen finden Sie unter [JavaScript\-Methoden](../javascript/reference/javascript-methods.md)  
  
## Erstellen eigener Funktionen  
 Sie können eigene Funktionen erstellen und dort einsetzen, wo Sie sie benötigen.  Eine Funktionsdefinition besteht aus einer Funktionsanweisung und einem Block von [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Anweisungen.  
  
 Die **checkTriplet**\-Funktion im folgenden Beispiel verwendet als Argumente die Seitenlängen eines Dreiecks.  Mit diesen Informationen berechnet die Funktion, ob es sich um ein rechtwinkliges Dreieck handelt. Dazu wird geprüft, ob die drei Zahlen den Satz des Pythagoras erfüllen \(das Quadrat der Länge der Hypotenuse eines rechtwinkligen Dreiecks ist gleich der Summe der Quadrate der beiden anderen Seiten\).  Die checkTriplet\-Funktion ruft eine von zwei weiteren Funktionen auf, um diesen Test durchzuführen.  
  
 Beachten Sie die Verwendung einer sehr kleinen Zahl \(„epsilon“\) als Testvariable in der Gleitkommaversion des Tests.  Wenn die Werte keine ganzen Zahlen sind, ist es aufgrund der bei Gleitkommaberechnungen auftretenden Ungenauigkeiten und Rundungsfehler nicht ratsam, direkt zu testen, ob die drei Zahlen den Satz des Pythagoras erfüllen.  Da ein direkter Test ein genaueres Ergebnis liefert, wird mit dem Code im folgenden Beispiel zunächst festgestellt, ob der direkte Test geeignet ist, dann wird der Test ggf. ausgeführt.  
  
```javascript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## Pfeilfunktionen  
 Die Pfeilfunktionssyntax `=>` stellt eine Kurzmethode zur Angabe einer anonymen Funktion dar.  Die Pfeilfunktionssyntax sieht folgendermaßen aus.  
  
```javascript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Werte auf der linken Seite des Pfeils, die in Klammern eingeschlossen sein können, geben die an die Funktion übergebenen Argumente an.  Für ein einzelnes Funktionsargument sind keine Klammern erforderlich.  Klammern sind erforderlich, wenn keine Argumente übergeben werden.  Die Funktionsdefinition auf der rechten Seite des Pfeils kann entweder ein Ausdruck sein, z. B. `v + 1`, oder ein Block von Anweisungen, die in geschweifte Klammern \({}\) eingeschlossen sind.  
  
> [!IMPORTANT]
>  Die Pfeilfunktionssyntax wird nur in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] unterstützt.  
  
 Der `new`\-Operator kann für eine Pfeilfunktion nicht verwendet werden.  
  
 Die folgenden Codebeispiele veranschaulichen die Verwendung der Pfeilfunktion mit Ausdrücken als Funktionsdefinitionen.  Im ersten Beispiel wird „v“ als Argument an den Ausdruck übergeben.  Im zweiten Beispiel werden „v“ und „i“ als Argumente an den Ausdruck übergeben.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 Das folgende Codebeispiel veranschaulicht die Verwendung der Pfeilfunktion mit einem Anweisungsblock.  
  
```javascript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 Im Gegensatz zu Standardfunktionen verwenden Pfeilfunktionen das gleiche lexikalische `this`\-Objekt wie der umgebende Code, wodurch die Notwendigkeit von Problemumgehungen wie z. B. `var self = this;` entfallen kann.  
  
 Das folgende Beispiel zeigt, dass der Wert des `this`\-Objekts innerhalb der Pfeilfunktion identisch mit dem Wert im umgebenden Code ist \(er verweist immer noch auf die `bob`\-Variable\).  
  
```javascript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Pfeilfunktionen verwenden auch das gleiche lexikalische `arguments`\-Objekt wie der umgebende Code \(ebenso wie das `this`\-Objekt\).  
  
<a name="Default"></a>   
## Standardparameter  
 Sie können einen Standardwert für einen Parameter in einer Funktion angeben, indem Sie ihm einen Anfangswert zuweisen.  Der Standardwert kann ein konstanter Wert oder ein Ausdruck sein.  
  
> [!IMPORTANT]
>  Standardparameter werden nur in [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
 Im folgenden Beispiel hat „y“ den Standardwert 10 und „z“ den Standardwert 20.  Die Funktion verwendet 10 als Wert von „y“, es sei denn, die aufrufende Funktion übergibt einen eindeutigen \(oder nicht definierten\) Wert als zweites Argument.  Die Funktion verwendet 20 als Wert von „z“, es sei denn, die aufrufende Funktion übergibt einen eindeutigen \(oder nicht definierten\) Wert als drittes Argument.  
  
```javascript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## Rest\-Parameter  
 Rest\-Parameter werden durch den Spread\-Operator \(                       ``  \) angegeben, und ermöglichen es, aufeinander folgende Argumente in einem Funktionsaufruf in ein Array umzuwandeln.  
  
 Rest\-Parameter machen das `arguments`\-Objekt überflüssig.  Rest\-Parameter unterscheiden sich in mehrerer Hinsicht vom `arguments`\-Objekt, z. B.:  
  
-   Ein Rest\-Parameter ist eine tatsächliche Arrayinstanz und unterstützt deshalb Vorgänge, die für ein Array ausgeführt werden können.  
  
-   Ein Rest\-Parameter enthält nur die aufeinander folgenden Argumente, die nicht als separate \(benannte\) Argumente übergeben werden \(im Gegensatz dazu enthält das `arguments`\-Objekt alle Argumente, die an die Funktion übergeben werden\).  
  
> [!IMPORTANT]
>  Rest\-Parameter und der Spread\-Operator werden nur in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] unterstützt.  
  
 Im folgenden Codebeispiel werden „hello“ und „true“ als Arraywerte übergeben und im y\-Parameter gespeichert.  Der Rest\-Parameter muss der letzte Parameter der Funktion sein.  
  
```javascript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Weitere Verwendungsmöglichkeiten des Spread\-Operators werden unter [Spread\-Operator](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) erläutert.  
  
## Siehe auch  
 [JavaScript\-Sprachreferenz](../javascript/javascript-language-reference.md)