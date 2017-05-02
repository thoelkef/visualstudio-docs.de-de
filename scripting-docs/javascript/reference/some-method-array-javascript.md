---
title: "some-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], some-Methode"
  - "some-Methode [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some-Methode (Array) (JavaScript)
Bestimmt, ob die angegebene Rückruffunktion für jedes Element eines Arrays `true` zurückgibt.  
  
## Syntax  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich.  Eine Funktion, die bis zu drei Argumente akzeptiert.  Die `some`\-Methode ruft die `callbackfn`\-Funktion für jedes Element in `array1` auf, bis die `callbackfn`\-Funktion `true` zurückgibt oder das Ende des Arrays erreicht wird.|  
|`thisArg`|Optional.  Ein Objekt, auf welches das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.|  
  
## Rückgabewert  
 `true`, wenn die `callbackfn`\-Funktion für jedes Arrayelement `true` zurückgibt; andernfalls `false`.  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `some`\-Methode ruft die `callbackfn`\-Funktion für jedes Arrayelement in aufsteigender Indexreihenfolge auf, bis die `callbackfn`\-Funktion `true` zurückgibt.  Wenn ein Element gefunden wird, das bewirkt, dass `callbackfn` `true` zurückgibt, dann gibt die `some`\-Methode sofort `true` zurück.  Wenn die Rückruffunktion für kein Element `true` zurückgibt, gibt die Methode `some` `false` zurück.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `some`\-Methode für jedes Objekt verwendet werden, das über eine `length`\-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
> [!NOTE]
>  Mit der [every\-Methode \(Array\)](../../javascript/reference/every-method-array-javascript.md) können Sie überprüfen, ob die Rückruffunktion für alle Elemente eines Arrays `true` zurückgibt.  
  
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
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `some`\-Methode beschrieben.  
  
|Bedingung nach dem Start der `some`\-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|--------------------------------------------------|---------------------------------------------------------|  
|Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Ein Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## Beispiel  
 Im folgenden Beispiel wird mit der `some`\-Methode ermittelt, ob Elemente in einem Array gerade sind.  
  
```javascript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie der `thisArg`\-Parameter verwendet wird, der ein Objekt angibt, auf das das `this`\-Schlüsselwort verweisen kann.  Er wird überprüft, ob Zahlen in einem Array außerhalb des Gültigkeitsbereichs liegen, der durch das übergebene Objekt angegeben wird.  
  
```javascript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [every\-Methode \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter\-Methode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map\-Methode \(Array\)](../../javascript/reference/map-method-array-javascript.md)