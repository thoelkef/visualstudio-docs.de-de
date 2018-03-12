---
title: Typeof-Operator (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof-Operator (JavaScript)
Gibt eine Zeichenfolge zurück, die den Datentyp eines Ausdrucks angibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Hinweise  
 Die *Ausdruck* Argument ist ein beliebiger Ausdruck, der für den Typinformationen ermittelt.  
  
 Der Operator `typeof` gibt die Typinformationen als Zeichenfolge zurück. Es gibt sechs mögliche Rückgabewerte für `typeof`: "number", "string", "boolean", "object", "function" und "undefined".  
  
 In der `typeof`-Syntax sind die Klammern optional.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel testet den Datentyp der Variablen.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird überprüft, ob deklarierte und nicht deklarierte Variablen des Datentyps `undefined` vorhanden sind.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Array.isArray-Funktion](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined-Konstante](../../javascript/reference/undefined-constant-javascript.md)   
 [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md)   
 [Datentypen](../../javascript/data-types-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)