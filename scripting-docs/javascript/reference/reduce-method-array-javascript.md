---
title: "reduce-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], reduce-Methode"
  - "Rückruffunktion, reduce-Methode [JavaScript]"
  - "reduce-Methode [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce-Methode (Array) (JavaScript)
Ruft die angegebene Rückruffunktion für alle Elemente in einem Array auf.  Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.  
  
## Syntax  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu vier Argumente akzeptiert.  Die `reduce`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Element im Array auf.|  
|`initialValue`|Optional.  Wenn der `initialValue`\-Parameter angegeben wird, wird er als Anfangswert der Akkumulation verwendet.  Der erste Aufruf der `callbackfn`\-Funktion stellt diesen Wert statt eines Arraywerts als Argument bereit.|  
  
## Rückgabewert  
 Das akkumulierte Ergebnis vom letzten Aufruf der Rückruffunktion.  
  
## Ausnahmen  
 Eine `TypeError` Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Das `callbackfn`\-Argument ist kein Funktionsobjekt.  
  
-   Das Array enthält keine Elemente, und `initialValue` wird nicht bereitgestellt.  
  
## Hinweise  
 Wenn `initialValue` angegeben wird, ruft die `reduce`\-Methode die `callbackfn`\-Funktion einmal für jedes im Array vorhandene Element in aufsteigender Indexreihenfolge auf.  Wenn `initialValue` nicht angegeben wird, ruft die `reduce`\-Methode die `callbackfn`\-Funktion für jedes Element ab dem zweiten Element auf.  
  
 Der Rückgabewert der Rückruffunktion wird als `previousValue`\-Argument für den nächsten Aufruf der Rückruffunktion bereitgestellt.  Der Rückgabewert des letzten Aufrufs der Rückruffunktion ist der Rückgabewert der Methode `reduce`.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
> [!NOTE]
>  Die [reduceRight\-Methode \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md) verarbeitet die Elemente in absteigender Indexreihenfolge.  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis vier Parameter angeben.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`previousValue`|Der Wert des vorherigen Aufrufs der Rückruffunktion.  Wenn `initialValue` für die `reduce`\-Methode angegeben wird, dann entspricht `previousValue` dem `initialValue`\-Wert des Elements, für das die Funktion zum ersten Mal aufgerufen wird.|  
|`currentValue`|Der Wert des aktuellen Arrayelements.|  
|`currentIndex`|Der numerische Index des aktuellen Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## Der erste Aufruf der Rückruffunktion  
 Die Werte, die beim ersten Aufruf der Rückruffunktion als Argumente bereitgestellt werden, hängen davon ab, ob die `reduce`\-Methode über ein `initialValue`\-Argument verfügt.  
  
 Wenn für die reduce\-Methode ein `initialValue`\-Argument angegeben wird:  
  
-   Das `previousValue`\-Argument ist `initialValue`.  
  
-   Das `currentValue`\-Argument ist der Wert des ersten Elements, das im Array vorhanden ist.  
  
 Wenn `initialValue` nicht angegeben wird:  
  
-   Das `previousValue`\-Argument ist der Wert des ersten Elements, das im Array vorhanden ist.  
  
-   Das `currentValue`\-Argument ist der Wert des zweiten Elements, das im Array vorhanden ist.  
  
## Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `reduce`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `reduce`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|----------------------------------------------------|---------------------------------------------------------|  
|Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Ein Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel werden Arraywerte zu einer Zeichenfolge verkettet und die Werte durch "::" voneinander getrennt.  Da kein Anfangswert für die `reduce`\-Methode bereitgestellt wird, wird im ersten Aufruf der Rückruffunktion "abc" als `previousValue`\-Argument und "def" als `currentValue`\-Argument verwendet.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## Beispiel  
 Im folgenden Beispiel werden die Werte eines Arrays hinzugefügt, nachdem sie gerundet wurden.  Die `reduce`\-Methode wird mit dem Anfangswert 0 aufgerufen.  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## Beispiel  
 Im folgenden Beispiel werden die Werte in einem Array hinzugefügt.  Die Parameter `currentIndex` und `array1` werden in der Rückruffunktion verwendet.  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array abgerufen, das nur die Werte enthält, die in einem anderen Array zwischen 1 und 10 sind.  Als Anfangswert wird für die `reduce`\-Methode ein leeres Array angegeben.  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [reduceRight\-Methode \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)