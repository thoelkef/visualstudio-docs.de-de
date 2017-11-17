---
title: Spread-Operator (...) (JavaScript) | Microsoft Docs
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>Spread-Operator (...) (JavaScript)
Ermöglicht Teilen eines Arrayliterals die Initialisierung aus einem iterierbaren Ausdruck (z. B. einem anderen Arrayliteral) oder einem Ausdruck das Erweitern auf mehrere Argumente (in Funktionsaufrufen).  
  
## <a name="syntax"></a>Syntax  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Parameter  
 `iterable`  
 Erforderlich. Ein iterierbares Objekt.  
  
 `arg0ToN`  
 Dies ist optional. Ein oder mehrere Elemente eines Arrayliterals.  
  
 `args`  
 Dies ist optional. Ein oder mehrere Argumente für eine Funktion.  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Iteratoren finden Sie unter [Iteratoren und Generatoren](../../javascript/advanced/iterators-and-generators-javascript.md). Weitere Informationen zur Verwendung des Spread-Operators als Rest-Parameter finden Sie unter [Funktionen](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des Spread-Operators der Verwendung der `concat`-Methode gegenübergestellt.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie der Spread-Operator in einem Funktionsaufruf verwendet wird. In diesem Beispiel werden zwei Arrayliterale mithilfe des Spread-Operators an die Funktion übergeben, und die Arrays werden auf mehrere Argumente erweitert.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Beispiel  
 Mithilfe von Spread-Operatoren können Sie Code, der zuvor die Verwendung von `apply` erforderte, vereinfachen.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)