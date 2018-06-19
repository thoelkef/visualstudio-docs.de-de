---
title: BIND-Methode (Funktion) (JavaScript) | Microsoft Docs
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634310"
---
# <a name="bind-method-function-javascript"></a>bind-Methode (Funktion) (JavaScript)
Eine gegebene Funktion erstellt eine gebundene Funktion, die über den gleichen Text wie die ursprüngliche Funktion verfügt. In der gebundenen Funktion wird das `this`-Objekt in das übergebene Objekt aufgelöst. Die gebundene Funktion weist die angegebenen ursprünglichen Parameter auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Parameter  
 `function`  
 Erforderlich. Ein Funktionsobjekt.  
  
 `thisArg`  
 Erforderlich. Ein Objekt, auf das das `this`-Schlüsselwort in der neuen Funktion verweisen kann.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Dies ist optional. Eine Liste von Argumenten, die an die neue Funktion übergeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine neue Funktion, die der `function`-Funktion entspricht, mit Ausnahme des `thisArg`-Objekts und des ursprünglichen Arguments.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn die angegebene `function` keine Funktion ist, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `bind`-Methode veranschaulicht.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel unterscheidet sich das `thisArg`-Objekt vom Objekt, das die ursprüngliche Methode enthält.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `arg1[,arg2[,argN]]]`-Argumente veranschaulicht. Die Funktion verwendet die Parameter, die in der `bind`-Methode als erster und zweiter Parameter angegeben sind. Alle beim Aufruf der gebundenen Funktion angegebenen Parameter werden als dritter und vierter (usw.) Parameter verwendet.  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Filter-Methode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Verwenden der Bind-Methode](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [HiLo JavaScript-Beispiel-app (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)