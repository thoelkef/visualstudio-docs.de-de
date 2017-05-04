---
title: "reduceRight-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], reduceRight-Methode"
  - "reduceRight-Methode [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight-Methode (Array) (JavaScript)
Ruft die angegebene Rückruffunktion für alle Elemente in einem Array in absteigender Reihenfolge auf.  Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.  
  
## Syntax  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu vier Argumente akzeptiert.  Die `reduceRight`\-Methode ruft die `callbackfn`\-Funktion für jedes Element im Array einmal auf.|  
|`initialValue`|Optional.  Wenn der `initialValue`\-Parameter angegeben wird, wird er als Anfangswert der Akkumulation verwendet.  Der erste Aufruf der `callbackfn`\-Funktion stellt diesen Wert statt eines Arraywerts als Argument bereit.|  
  
## Rückgabewert  
 Ein Objekt, das das akkumulierte Ergebnis vom letzten Aufruf der Rückruffunktion enthält.  
  
## Ausnahmen  
 Eine `TypeError` Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Das `callbackfn`\-Argument ist kein Funktionsobjekt.  
  
-   Das Array enthält keine Elemente, und `initialValue` wird nicht bereitgestellt.  
  
## Hinweise  
 Wenn `initialValue` angegeben wird, ruft die `reduceRight`\-Methode die `callbackfn`\-Funktion für jedes im Array vorhandene Element in absteigender Indexreihenfolge einmal auf.  Wenn `initialValue` nicht angegeben wird, ruft die `reduceRight`\-Methode die `callbackfn`\-Funktion für jedes Element ab dem vorletzten Element in absteigender Indexreihenfolge auf.  
  
 Der Rückgabewert der Rückruffunktion wird als `previousValue`\-Argument für den nächsten Aufruf der Rückruffunktion bereitgestellt.  Der Rückgabewert des letzten Aufrufs der Rückruffunktion ist der Rückgabewert der Methode `reduceRight`.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Um ein Ergebnis in aufsteigender Indexreihenfolge zu akkumulieren, verwenden Sie [reduce\-Methode \(Array\)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis vier Parameter angeben.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`previousValue`|Der Wert des vorherigen Aufrufs der Rückruffunktion.  Wenn `initialValue` für die `reduceRight`\-Methode angegeben wird, dann entspricht `previousValue` dem `initialValue`\-Wert des Elements, für das die Funktion zum ersten Mal aufgerufen wird.|  
|`currentValue`|Der Wert des aktuellen Arrayelements.|  
|`currentIndex`|Der numerische Index des aktuellen Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## Der erste Aufruf der Rückruffunktion  
 Die Werte, die beim ersten Aufruf der Rückruffunktion als Argumente bereitgestellt werden, hängen davon ab, ob die `reduceRight`\-Methode über ein `initialValue`\-Argument verfügt.  
  
 Wenn `initialValue` für die `reduceRight`\-Methode angegeben wird:  
  
-   Das `previousValue`\-Argument ist `initialValue`.  
  
-   Das `currentValue`\-Argument ist der Wert des letzten Elements, das im Array vorhanden ist.  
  
 Wenn `initialValue` nicht angegeben wird:  
  
-   Das `previousValue`\-Argument ist der Wert des letzten Elements, das im Array vorhanden ist.  
  
-   Das `currentValue`\-Argument ist der Wert des vorletzten Elements, das im Array vorhanden ist.  
  
## Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `reduceRight`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `reduceRight`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|---------------------------------------------------------|---------------------------------------------------------|  
|Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Ein Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel werden Arraywerte zu einer Zeichenfolge verkettet und die Werte durch "::" voneinander getrennt.  Da kein Anfangswert für die `reduceRight`\-Methode bereitgestellt wird, wird im ersten Aufruf der Rückruffunktion "456" als `previousValue`\-Argument und "123" als `currentValue`\-Argument verwendet.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Summe der Quadrate der Arrayelemente ermittelt.  Die `reduceRight`\-Methode wird mit dem Anfangswert 0 aufgerufen.  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## Beispiel  
 Im folgenden Beispiel werden die Elemente eines Arrays abgerufen, deren Werte zwischen 1 und 10 liegen.  Als Anfangswert wird für die `reduceRight`\-Methode ein leeres Array angegeben.  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## Beispiel  
 Die `reduceRight`\-Methode kann auf eine Zeichenfolge angewendet werden.  Im folgenden Beispiel wird gezeigt, wie diese Methode verwendet wird, um die Zeichen einer Zeichenfolge umzukehren.  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [reduce\-Methode \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)