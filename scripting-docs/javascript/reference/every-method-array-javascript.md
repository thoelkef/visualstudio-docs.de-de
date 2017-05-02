---
title: "every-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], every-Methode"
  - "every-Methode"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every-Methode (Array) (JavaScript)
Bestimmt, ob alle Member eines Arrays den angegebenen Test erfüllen.  
  
## Syntax  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu drei Argumente akzeptiert.  Die `every`\-Methode ruft die `callbackfn`\-Funktion für jedes Element in `array1` auf, bis die `callbackfn`\-Funktion `false` zurückgibt oder das Ende des Arrays erreicht wird.|  
|`thisArg`|Optional.  Ein Objekt, auf welches das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.|  
  
## Rückgabewert  
 `true`, wenn die `callbackfn`\-Funktion für alle Arrayelemente `true` zurückgibt; andernfalls `false`.  Wenn das Array keine Elemente enthält, gibt die `every`\-Methode `true` zurück.  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `every`\-Methode ruft die `callbackfn`\-Funktion einmal für jedes Arrayelement in aufsteigender Indexreihenfolge auf, bis die `callbackfn`\-Funktion `false` zurückgibt.  Wenn ein Element gefunden wird, das bewirkt, dass `callbackfn` `false` zurückgibt, dann gibt die `every`\-Methode sofort `false` zurück.  Andernfalls gibt die `every`\-Methode `true` zurück.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `every`\-Methode für jedes Objekt verwendet werden, das über eine `length`\-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
> [!NOTE]
>  Mit der [some\-Methode \(Array\)](../../javascript/reference/some-method-array-javascript.md) können Sie überprüfen, ob die Rückruffunktion für Elemente eines Arrays `true` zurückgibt.  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, array1)`  
  
 Sie können die Rückruffunktion mit bis zu drei Parametern deklarieren.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|Rückrufparameter|Definition|  
|----------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `every`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `every`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|---------------------------------------------------|---------------------------------------------------------|  
|Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Ein Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `every`\-Methode veranschaulicht.  
  
```javascript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `thisArg`\-Arguments veranschaulicht, mit dem ein Objekt angegeben wird, auf das das `this`\-Schlüsselwort verweisen kann.  
  
```javascript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [some\-Methode \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter\-Methode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)