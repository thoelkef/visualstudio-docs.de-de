---
title: Filter-Methode (Array) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="filter-method-array-javascript"></a>filter-Methode (Array) (JavaScript)
Gibt die Elemente eines Arrays, die in einer Rückruffunktion angegebene Bedingung erfüllen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich. Eine Funktion, die bis zu drei Argumente akzeptiert. Die `filter`-Methode ruft die `callbackfn`-Funktion einmal für jedes Element im Array auf.|  
|`thisArg`|Dies ist optional. Ein Objekt, auf welches das `this`-Schlüsselwort in der `callbackfn`-Funktion verweisen kann. Wird `thisArg` nicht angegeben, wird `undefined` als `this`-Wert verwendet.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein neues Array, das alle Werte enthält, für das die Rückruffunktion zurückgibt `true`. Wenn die Rückruffunktion zurückgegeben `false` für alle Elemente des `array1`, die Länge des neuen Arrays ist 0.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn es sich beim `callbackfn`-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `filter`-Methode ruft die `callbackfn`-Funktion einmal für jedes Element im Array in aufsteigender Indexreihenfolge auf. Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `filter`-Methode für jedes Objekt verwendet werden, das über eine `length`-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
## <a name="callback-function-syntax"></a>Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, array1)`  
  
 Beim Deklarieren der Rückruffunktion können bis zu drei Parameter verwendet werden.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|-----------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## <a name="modifying-the-array-object"></a>Ändern des Arrayobjekts  
 Die `filter`-Methode ändert das Originalarray nicht direkt, dies ist jedoch über die Rückruffunktion möglich. In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `filter`-Methode beschrieben.  
  
|Bedingung nach dem Start der `filter`-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|------------------------------------------------|------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `filter`-Methode gezeigt.  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel enthält das `callbackfn`-Argument den Code der Rückruffunktion.  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Namen von Eigenschaften, die mit dem Buchstaben "Css", in beginnen der `window` DOM-Objekt.  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `thisArg`-Arguments veranschaulicht, mit dem ein Objekt angegeben wird, auf das das `this`-Schlüsselwort verweisen kann.  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>Beispiel  
 Die `filter` -Methode kann in eine Zeichenfolge anstelle eines Arrays angewendet werden. Das folgende Beispiel zeigt die dazu erforderliche Vorgehensweise.  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)   
 [Map-Methode (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach-Methode (Array)](../../javascript/reference/foreach-method-array-javascript.md)