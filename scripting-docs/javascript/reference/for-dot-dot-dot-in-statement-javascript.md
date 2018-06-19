---
title: for... in-Anweisung (JavaScript) | Microsoft Docs
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636730"
---
# <a name="forin-statement-javascript"></a>for...in-Anweisung (JavaScript)
Führt eine oder mehrere Anweisungen für jede Eigenschaft eines Objekts oder der jedes Element eines Arrays.  
  
## <a name="syntax"></a>Syntax  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parameter  
 `variable`  
 Erforderlich. Eine Variable, die Namen einer Eigenschaft des kann `object` oder Elementindex ein `array`.  
  
 `object`, `array`  
 Dies ist optional. Ein Objekt oder Array, das durchlaufen.  
  
 `statements`  
 Dies ist optional. Eine oder mehrere Anweisungen für jede Eigenschaft des auszuführenden `object` oder jedes Elements des `array`. Kann eine Verbundanweisung sein.  
  
## <a name="remarks"></a>Hinweise  
 Am Anfang jeder Iteration einer Schleife, die den Wert der `variable` ist der nächste Eigenschaftsname des `object` oder das nächste Elementindex von `array`. Anschließend können Sie `variable` in Anweisungen innerhalb der Schleife, um die Eigenschaft der `object` oder das Element eines `array`.  
  
 Die Eigenschaften eines Objekts werden nicht auf bestimmte Weise zugewiesen werden. Sie können keine bestimmte Eigenschaft über seinen Index nur durch den Namen der Eigenschaft angeben.  
  
 Durchlaufen eines Arrays wird in der Reihenfolge der Elemente, d. h. 0, 1, 2 ausgeführt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...in` Anweisung mit einem Objekt, das als assoziatives Array verwendet.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel veranschaulicht die Verwendung der `for ... in` Anweisung durchlaufen einer `Array` -Objekt, das Expando-Eigenschaften.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Verwenden der `Enumerator` Objekt, das die Elemente einer Auflistung zu durchlaufen.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [while-Anweisung](../../javascript/reference/while-statement-javascript.md)