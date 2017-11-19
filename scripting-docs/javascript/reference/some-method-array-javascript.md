---
title: Some-Methode (Array) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some-Methode (Array) (JavaScript)
Bestimmt, ob die angegebene Rückruffunktion zurückgibt `true` für jedes Element eines Arrays.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`callbackfn`|Erforderlich. Eine Funktion, die bis zu drei Argumente akzeptiert. Die `some` Methodenaufrufe der `callbackfn` Funktion für jedes Element im `array1` bis der `callbackfn` gibt `true`, oder bis zum Ende des Arrays.|  
|`thisArg`|Dies ist optional. Ein Objekt, auf welches das `this`-Schlüsselwort in der `callbackfn`-Funktion verweisen kann. Wird `thisArg` nicht angegeben, wird `undefined` als `this`-Wert verwendet.|  
  
## <a name="return-value"></a>Rückgabewert  
 `true`Wenn die `callbackfn` -Funktion gibt `true` für jedes Arrayelement; anderenfalls `false`.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn es sich beim `callbackfn`-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `some` Methodenaufrufe der `callbackfn` Funktion auf jedes Arrayelement, in aufsteigender Indexreihenfolge, bis die `callbackfn` -Funktion zurückgegeben `true`. Wenn ein Element, das bewirkt, dass `callbackfn` zurückzugebenden `true` gefunden wird, wird die `some` sofort Methodenrückgabe `true`. Wenn der Rückruf nicht zurückgibt `true` auf ein beliebiges Element der `some` -Methode zurückkehrt `false`.  
  
 Die Rückruffunktion wird nicht für fehlende Elemente des Arrays aufgerufen.  
  
 Außer für Arrayobjekte kann die `some`-Methode für jedes Objekt verwendet werden, das über eine `length`-Eigenschaft und numerisch indizierte Eigenschaftennamen verfügt.  
  
> [!NOTE]
>  Sie können die [every-Methode (Array)](../../javascript/reference/every-method-array-javascript.md) zu überprüfen, ob die Rückruffunktion zurückgegeben `true` für alle Elemente eines Arrays.  
  
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
  
 In der folgenden Tabelle werden die Ergebnisse der Änderung des Arrayobjekts nach dem Start der `some`-Methode beschrieben.  
  
|Bedingung nach dem Start der `some`-Methode|Wurde das Element an die Rückruffunktion übergeben?|  
|----------------------------------------------|------------------------------------------|  
|Das Element wird der ursprünglichen Länge des Arrays hinzugefügt.|Nein.|  
|Das Element wird hinzugefügt, um ein fehlendes Element des Arrays zu ersetzen.|Ja, wenn dieser Index noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird geändert.|Ja, wenn dieses Element noch nicht an die Rückruffunktion übergeben wurde.|  
|Das Element wird aus dem Array gelöscht.|Nein, es sei denn, dieses Element wurde bereits an die Rückruffunktion übergeben.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `some` Methode, um alle Elemente in einem Array ermitteln, ob sind selbst.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die `thisArg` -Parameter, der ein Objekt, mit dem gibt an, die `this` -Schlüsselwort verweisen kann. Er überprüft, ob die Zahlen in einem Array außerhalb des Bereichs von übergebenen Objekts bereitgestellt werden  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [EVERY-Methode (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [Filter-Methode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [map-Methode (Array)](../../javascript/reference/map-method-array-javascript.md)