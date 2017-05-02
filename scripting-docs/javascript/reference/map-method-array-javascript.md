---
title: "map-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], map-Methode"
  - "map-Methode [JavaScript]"
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# map-Methode (Array) (JavaScript)
Ruft für jedes Element eines Arrays eine definierte Rückruffunktion auf und gibt ein Array zurück, das die Ergebnisse enthält.  
  
## Syntax  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu drei Argumente akzeptiert.  Die `map`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Element im Array auf.|  
|`thisArg`|Optional.  Ein Objekt, auf welches das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.|  
  
## Rückgabewert  
 Ein neues Array, in dem jedes Element der Rückgabewert der Rückruffunktion für das zugeordnete ursprüngliche Arrayelement ist.  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `map`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Element im Array in aufsteigender Indexreihenfolge auf.  Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `map`\-Methode für jedes Objekt verwendet werden, das über eine `length`\-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
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
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `map`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `map`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|-------------------------------------------------|---------------------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `map`\-Methode veranschaulicht.  
  
```javascript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `thisArg`\-Arguments veranschaulicht, mit dem ein Objekt angegeben wird, auf das das `this`\-Schlüsselwort verweisen kann.  
  
```javascript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## Beispiel  
 Im folgenden Beispiel wird eine integrierte [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Methode als Rückruffunktion verwendet.  
  
```javascript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## Beispiel  
 Die `map`\-Methode kann auf eine Zeichenfolge angewendet werden.  Dies wird anhand des folgenden Beispiels veranschaulicht.  
  
```javascript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [JavaScript\-Methoden](../../javascript/reference/javascript-methods.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)   
 [filter\-Methode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach\-Methode \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Beispiel\-App für Hilo JavaScript \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)