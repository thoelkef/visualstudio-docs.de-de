---
title: reduce-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76279f66f8e3180fdebd73b83eb31c7368cefc75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="reduce-method-array-javascript"></a>reduce-Methode (Array) (JavaScript)
Ruft die angegebene Rückruffunktion für alle Elemente in einem Array an. Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich. Eine Funktion, die bis zu vier Argumente akzeptiert. Die `reduce`-Methode ruft die `callbackfn`-Funktion einmal für jedes Element im Array auf.|  
|`initialValue`|Dies ist optional. Wenn `initialValue` angegeben wird, es wird als Anfangswert verwendet, um die Kumulation zu starten. Der erste Aufruf der `callbackfn` -Funktion bietet dieser Wert als Argument anstelle eines Arraywerts.|  
  
## <a name="return-value"></a>Rückgabewert  
 Das akkumulierte Ergebnis aus dem letzten Aufruf der Rückruffunktion.  
  
## <a name="exceptions"></a>Ausnahmen  
 Ein `TypeError` Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Die `callbackfn` -Argument nicht um ein Funktionsobjekt handelt.  
  
-   Das Array enthält keine Elemente und `initialValue` wird nicht bereitgestellt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein `initialValue` angegeben ist, die `reduce` Methodenaufrufe der `callbackfn` -Funktion einmal für jedes Element im Array in aufsteigender Indexreihenfolge. Wenn ein `initialValue` nicht angegeben wird, die `reduce` Methodenaufrufe der `callbackfn` Funktion auf jedes Element, das zweite Element ab.  
  
 Der Rückgabewert der Rückruffunktion bereitgestellt wird, als die `previousValue` Argument, das beim nächsten Aufruf der Rückruffunktion. Der Rückgabewert der dem letzten Aufruf der Rückruffunktion ist der Rückgabewert von der `reduce` Methode.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
> [!NOTE]
>  Die [ReduceRight-Methode (Array)](../../javascript/reference/reduceright-method-array-javascript.md) verarbeitet die Elemente in absteigender Reihenfolge des Index.  
  
## <a name="callback-function-syntax"></a>Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis zu vier Parameter.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|-----------------------|----------------|  
|`previousValue`|Der Wert aus dem vorherigen Aufruf der Rückruffunktion. Wenn ein `initialValue` wird bereitgestellt, um die `reduce` -Methode, die `previousValue` ist `initialValue` zum ersten Mal die Funktion aufgerufen wird.|  
|`currentValue`|Der Wert des aktuellen Arrayelements.|  
|`currentIndex`|Der numerische Index des aktuellen Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## <a name="first-call-to-the-callback-function"></a>Ersten Aufruf der Rückruffunktion  
 Zum ersten Mal die Rückruffunktion aufgerufen wird, die als Argumente bereitgestellten Werte abhängig, ob die `reduce` Methode verfügt über ein `initialValue` Argument.  
  
 Wenn ein `initialValue` wird bereitgestellt, um die Reduce-Methode:  
  
-   Das `previousValue`-Argument lautet `initialValue`.  
  
-   Die `currentValue` Argument ist der Wert des ersten Elements im Array vorhanden.  
  
 Wenn ein `initialValue` nicht zur Verfügung gestellt:  
  
-   Die `previousValue` Argument ist der Wert des ersten Elements im Array vorhanden.  
  
-   Die `currentValue` Argument ist der Wert des zweiten Elements im Array vorhanden.  
  
## <a name="modifying-the-array-object"></a>Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `reduce`-Methode beschrieben.  
  
|Bedingung nach dem Start der `reduce`-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|------------------------------------------------|------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird Arraywerte in eine Zeichenfolge, die einzelnen Werte mit "::". Da kein Anfangswert, um bereitgestellt wird die `reduce` Methode, hat der erste Aufruf der Rückruffunktion wie "Abc" die `previousValue` Argument und "Def" als die `currentValue` Argument.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Werte eines Arrays aus, nachdem sie haben gerundet wurde. Die `reduce` Methode mit einem Anfangswert von 0 aufgerufen wird.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel fügt die Werte in einem Array. Die `currentIndex` und `array1` Parameter werden in der Rückruffunktion verwendet.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Array, das nur die Werte enthält, die zwischen 1 und 10 in einem anderen Array sind. Der Anfangswert bereitgestellt, um die `reduce` Methode ist ein leeres Array.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [reduceRight-Methode (Array)](../../javascript/reference/reduceright-method-array-javascript.md)