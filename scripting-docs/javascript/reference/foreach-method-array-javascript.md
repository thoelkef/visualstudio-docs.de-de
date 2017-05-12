---
title: "forEach-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], forEach-Methode"
  - "Rückruffunktion, forEach-Methode [JavaScript]"
  - "forEach-Methode [JavaScript]"
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# forEach-Methode (Array) (JavaScript)
Führt die angegebene Aktion für jedes Element in einem Array aus.  
  
## Syntax  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu drei Argumente akzeptiert.  `forEach` ruft die `callbackfn`\-Funktion für jedes Element im Array einmal auf.|  
|`thisArg`|Optional.  Ein Objekt, auf welches das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.|  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `forEach`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Element im Array in aufsteigender Indexreihenfolge auf.  Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `forEach`\-Methode für jedes Objekt verwendet werden, das über eine `length`\-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, array1)`  
  
 Beim Deklarieren der Rückruffunktion können bis zu drei Parameter verwendet werden.  
  
 Die Rückruffunktionsparameter lauten wie folgt:  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## Ändern des Arrayobjekts  
 Die `forEach`\-Methode ändert das Originalarray nicht direkt, dies ist jedoch über die Rückruffunktion möglich.  In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `forEach`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `forEach`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|-----------------------------------------------------|---------------------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `forEach`\-Methode veranschaulicht.  
  
```javascript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## Beispiel  
 Im folgenden Beispiel enthält das `callbackfn`\-Argument den Code der Rückruffunktion.  
  
```javascript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des `thisArg`\-Arguments, das ein Objekt angibt, auf das mit dem `this`\-Schlüsselwort verwiesen werden kann.  
  
```javascript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [filter\-Methode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map\-Methode \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [some\-Methode \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)   
 [Beispiel\-App für Hilo JavaScript \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)