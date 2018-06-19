---
title: EVERY-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637400"
---
# <a name="every-method-array-javascript"></a>every-Methode (Array) (JavaScript)
Bestimmt, ob alle Elemente eines Arrays des angegebenen Tests erfüllen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich. Eine Funktion, die bis zu drei Argumente akzeptiert. Die `every` Methodenaufrufe der `callbackfn` Funktion für jedes Element im `array1` bis der `callbackfn` gibt `false`, oder bis zum Ende des Arrays.|  
|`thisArg`|Dies ist optional. Ein Objekt, auf welches das `this`-Schlüsselwort in der `callbackfn`-Funktion verweisen kann. Wird `thisArg` nicht angegeben, wird `undefined` als `this`-Wert verwendet.|  
  
## <a name="return-value"></a>Rückgabewert  
 `true`Wenn die `callbackfn` -Funktion gibt `true` für alle Elemente array hingegen `false`. Wenn das Array verfügt über keine Elemente der `every` -Methode zurückkehrt `true`.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn es sich beim `callbackfn`-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `every` Methodenaufrufe der `callbackfn` -Funktion einmal für jedes Arrayelement, in aufsteigender Indexreihenfolge, bis die `callbackfn` -Funktion zurückgegeben `false`. Wenn ein Element, das bewirkt, dass `callbackfn` zurückzugebenden `false` gefunden wird, wird die `every` sofort Methodenrückgabe `false`. Andernfalls die `every` -Methode zurückkehrt `true`.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `every`-Methode für jedes Objekt verwendet werden, das über eine `length`-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
> [!NOTE]
>  Sie können die [some-Methode (Array)](../../javascript/reference/some-method-array-javascript.md) zu überprüfen, ob die Rückruffunktion zurückgegeben `true` für jedes Element eines Arrays.  
  
## <a name="callback-function-syntax"></a>Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, array1)`  
  
 Sie können die Rückruffunktion mit bis zu drei Parameter deklarieren.  
  
 In der folgenden Tabelle werden die Parameter für die Rückruffunktion aufgeführt.  
  
|"Callback"-Parameter|Definition|  
|------------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`array1`|Das Arrayobjekt, in dem das Element enthalten ist.|  
  
## <a name="modifying-the-array-object"></a>Ändern des Arrayobjekts  
 Das Arrayobjekt kann durch die Rückruffunktion geändert werden.  
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `every`-Methode beschrieben.  
  
|Bedingung nach dem Start der `every`-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|-----------------------------------------------|------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `every`-Methode veranschaulicht.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `thisArg`-Arguments veranschaulicht, mit dem ein Objekt angegeben wird, auf das das `this`-Schlüsselwort verweisen kann.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Some-Methode (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Filter-Methode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)