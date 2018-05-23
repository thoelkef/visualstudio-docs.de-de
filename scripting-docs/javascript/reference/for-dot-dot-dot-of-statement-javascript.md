---
title: for...-Anweisung (JavaScript) | Microsoft Docs
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
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
 Erforderlich. Ein iterierbares Objekt wie z. B. ein `Array`, `Map`, `Set`, oder ein Objekt, implementiert die [Iterator-Schnittstellen](../../javascript/advanced/iterators-and-generators-javascript.md).  
  
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