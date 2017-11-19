---
title: ReduceRight-Methode (Array) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="reduceright-method-array-javascript"></a>reduceRight-Methode (Array) (JavaScript)
Ruft die angegebene Rückruffunktion für alle Elemente in einem Array, in absteigender Reihenfolge. Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich. Eine Funktion, die bis zu vier Argumente akzeptiert. Die `reduceRight`-Methode ruft die `callbackfn`-Funktion einmal für jedes Element im Array auf.|  
|`initialValue`|Dies ist optional. Wenn `initialValue` angegeben wird, es wird als Anfangswert verwendet, um die Kumulation zu starten. Der erste Aufruf der `callbackfn` -Funktion bietet dieser Wert als Argument anstelle eines Arraywerts.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Objekt, das akkumulierte Ergebnis aus dem letzten Aufruf der Rückruffunktion enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 Ein `TypeError` Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Die `callbackfn` -Argument nicht um ein Funktionsobjekt handelt.  
  
-   Das Array enthält keine Elemente und `initialValue` wird nicht bereitgestellt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein `initialValue` angegeben ist, die `reduceRight` Methodenaufrufe der `callbackfn` -Funktion einmal für jedes Element im Array, in absteigender Reihenfolge des Index. Wenn kein `initialValue` angegeben ist, die `reduceRight` Methodenaufrufe der `callbackfn` Funktion auf jedes Element, mit dem zweiten vorletztes-Element, in absteigender Reihenfolge des Index ab.  
  
 Der Rückgabewert der Rückruffunktion bereitgestellt wird, als die `previousValue` Argument, das beim nächsten Aufruf der Rückruffunktion. Der Rückgabewert der dem letzten Aufruf der Rückruffunktion ist der Rückgabewert von der `reduceRight` Methode.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Um ein Ergebnis in aufsteigender Indexreihenfolge kumuliert werden, verwenden die [reduce-Methode (Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis zu vier Parameter.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|-----------------------|----------------|  
|`previousValue`|Der Wert aus dem vorherigen Aufruf der Rückruffunktion. Wenn ein `initialValue` wird bereitgestellt, um die `reduceRight` -Methode, die `previousValue` ist `initialValue` zum ersten Mal die Funktion aufgerufen wird.|  
|`currentValue`|Der Wert des aktuellen Arrayelements.|  
|`currentIndex`|Der numerische Index des aktuellen Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## <a name="first-call-to-the-callback-function"></a>Ersten Aufruf der Rückruffunktion  
 Zum ersten Mal die Rückruffunktion aufgerufen wird, die als Argumente bereitgestellten Werte abhängig, ob die `reduceRight` Methode verfügt über ein `initialValue` Argument.  
  
 Wenn ein `initialValue` wird bereitgestellt, um die `reduceRight` Methode:  
  
-   Das `previousValue`-Argument lautet `initialValue`.  
  
-   Die `currentValue` Argument ist der Wert des letzten Elements im Array vorhanden.  
  
 Wenn ein `initialValue` nicht zur Verfügung gestellt:  
  
-   Die `previousValue` Argument ist der Wert des letzten Elements im Array vorhanden.  
  
-   Die `currentValue` Argument ist der Wert des zweiten vorletztes Elements im Array vorhanden.  
  
## <a name="modifying-the-array-object"></a>Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `reduceRight`-Methode beschrieben.  
  
|Bedingung nach dem Start der `reduceRight`-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|-----------------------------------------------------|------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird Arraywerte in eine Zeichenfolge, die einzelnen Werte mit "::". Da kein Anfangswert, um bereitgestellt wird die `reduceRight` -Methode, der erste Aufruf der Rückruffunktion hat 456 als der `previousValue` Argument und 123 als der `currentValue` Argument.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel sucht die Summe der Quadrate der Elemente des Arrays. Die `reduceRight` Methode mit einem Anfangswert von 0 aufgerufen wird.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel ruft die Elemente eines Arrays, dessen Werte zwischen 1 und 10 sind. Der Anfangswert bereitgestellt, um die `reduceRight` Methode ist ein leeres Array.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Die `reduceRight`-Methode kann auf eine Zeichenfolge angewendet werden. Im folgende Beispiel wird gezeigt, wie diese Methode verwendet die Zeichen in einer Zeichenfolge umgekehrt wird.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [reduce-Methode (Array)](../../javascript/reference/reduce-method-array-javascript.md)