---
title: "filter-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], Filtermethode"
  - "Filtermethode [JavaScript]"
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# filter-Methode (Array) (JavaScript)
Gibt die Elemente eines Arrays zurück, welche die Bedingung erfüllen, die in einer Rückruffunktion angegeben sind.  
  
## Syntax  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu drei Argumente akzeptiert.  Die `filter`\-Methode ruft einmal für jedes Element im Array die `callbackfn`\-Funktion auf.|  
|`thisArg`|Optional.  Ein Objekt, auf welches das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.|  
  
## Rückgabewert  
 Ein neues Array, das alle Werte enthält, für welche die Rückruffunktion `true` zurückgibt.  Wenn die Rückruffunktion für alle Elemente von `array1` den Wert `false` zurückgibt, ist die Länge des neuen Arrays 0 \(null\).  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `filter`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Element im Array in aufsteigender Indexreihenfolge auf.  Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `filter`\-Methode für jedes Objekt verwendet werden, das über eine `length`\-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, array1)`  
  
 Beim Deklarieren der Rückruffunktion können bis zu drei Parameter verwendet werden.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## Ändern des Arrayobjekts  
 Die `filter`\-Methode ändert das Originalarray nicht direkt, dies ist jedoch über die Rückruffunktion möglich.  In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `filter`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `filter`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|----------------------------------------------------|---------------------------------------------------------|  
|Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Ein Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `filter`\-Methode veranschaulicht.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel enthält das `callbackfn`\-Argument den Code der Rückruffunktion.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel werden die Namen von Eigenschaften angezeigt, die im `window`\-DOM\-Objekt mit den Buchstaben "css" beginnen.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `thisArg`\-Arguments veranschaulicht, mit dem ein Objekt angegeben wird, auf das das `this`\-Schlüsselwort verweisen kann.  
  
```javascript  
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
  
## Beispiel  
 Die `filter`\-Methode kann anstelle eines Arrays auf eine Zeichenfolge angewendet werden.  Im folgenden Beispiel wird erläutert, wie Sie hierzu vorgehen:  
  
```javascript  
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
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)   
 [map\-Methode \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach\-Methode \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)