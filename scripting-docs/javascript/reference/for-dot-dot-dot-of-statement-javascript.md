---
title: for...-Anweisung (JavaScript) | Microsoft Docs
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>for...of-Anweisung (JavaScript)
Führt eine oder mehrere Anweisungen für jeden Wert eines Iterators aus, der von einem iterable-Wert abgerufen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parameter  
 `variable`  
 Erforderlich. Eine Variable, die einen beliebigen Eigenschaftswert von `object` sein kann.  
  
 `object`  
 Erforderlich. Ein iterierbares Objekt wie z. B. ein `Array`, `Map`, `Set`, oder ein Objekt, implementiert die [Iterator-Schnittstellen](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Dies ist optional. Eine oder mehrere auszuführende Anweisungen für jeden Wert von `object`. Kann eine Verbundanweisung sein.  
  
## <a name="remarks"></a>Hinweise  
 Am Anfang jeder Iteration einer Schleife, ist der Wert der `variable` der nächste Eigenschaftswert der `object`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...of`-Anweisung in einem Array.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...of`-Anweisung in einem `Map`Objekt.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [for... in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [while-Anweisung](../../javascript/reference/while-statement-javascript.md)