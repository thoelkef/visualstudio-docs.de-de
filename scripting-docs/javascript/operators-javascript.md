---
title: Operatoren (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>Operatoren (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verfügt über ein breites Spektrum an Operatoren. Dazu gehören arithmetische, logische und bitweise Operatoren, der Zuweisungsoperator sowie weitere Operatoren. Erklärungen und Beispiele finden Sie in den jeweiligen Themen zu bestimmen Operatoren.  
  
## <a name="computational-operators"></a>Rechenoperatoren  
  
|Beschreibung|Symbol|  
|-----------------|------------|  
|[Unäre Negation](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Inkrement](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Dekrement](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Multiplikation](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[Division](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Arithmetischer Modulo](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Addition](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Subtraktion](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Logische Operatoren  
  
|Beschreibung|Symbol|  
|-----------------|------------|  
|[logisches NOT](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Kleiner als](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Größer als](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Kleiner gleich](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Größer gleich](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Gleichheit](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Ungleichheit](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[Logisches AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[Logisches OR](../javascript/reference/logical-or-operator-decrement-javascript.md)||||  
|[Bedingt (ternär)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Komma](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Strikte Gleichheit](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Strikte Ungleichheit](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Bitweise Operatoren  
  
|Beschreibung|Symbol|  
|-----------------|------------|  
|[Bitweises NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Bitweise Linksverschiebung](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Bitweise Rechtsverschiebung](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Vorzeichenlose Rechtsverschiebung](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[Bitweises AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Bitweises XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Bitweises OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Zuweisungsoperatoren  
  
|Beschreibung|Symbol|  
|-----------------|------------|  
|[Zuweisung](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Verbundzuweisung](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (wie += und &=)|  
  
## <a name="miscellaneous-operators"></a>Verschiedene Operatoren  
  
|Beschreibung|Symbol|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|Löschen|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|neu|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|Zoll|  
  
## <a name="equality-and-strict-equality"></a>Gleichheit und strikte Gleichheit  
 Der Unterschied zwischen == (Gleichheit) und === (strikte Gleichheit) besteht darin, dass der Gleichheitsoperator Werte unterschiedlicher Typen umwandelt, bevor die Gleichheit überprüft wird. Wenn z.B. die Zeichenfolge "1" mit der Zahl 1 verglichen wird, dann wird TRUE zurückgegeben. Der strikte Gleichheitsoperator wandelt keine Werte in unterschiedliche Typen um, also ist die Zeichenfolge "1" nicht mit der Zahl 1 gleichwertig.  
  
 Primitive Zeichenfolgen, Zahlen und boolesche Werte werden nach Wert verglichen. Wenn sie über denselben Wert verfügen, sind sie gleich. Objekte (einschließlich der Objekte`Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` und `RegExp`) werden nach Verweis verglichen. Auch wenn zwei Variablen dieser Typen über denselben Wert verfügen, sind sie nur gleich, wenn sie auf dasselbe Objekt verweisen.  
  
 Zum Beispiel:  
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```