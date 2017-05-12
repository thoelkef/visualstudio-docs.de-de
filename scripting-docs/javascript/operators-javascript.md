---
title: "Operatoren (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, Operatoren"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Operatoren (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verfügt über eine umfassende Auswahl von arithmetischen Operatoren. Neben einigen nicht kategorisierbaren Operatoren sind dies u. a. arithmetische, logische, bitweise und Zuweisungsoperatoren.  Weitere Erläuterungen und Beispiele finden Sie in den Themen zu bestimmten Operatoren.  
  
## Arithmetische Operatoren  
  
|Beschreibung|Symbol|  
|------------------|------------|  
|[Unäre Negation](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[Increment](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[Decrement](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[Multiplikation](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[Division](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[Modulo](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Addition](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[Subtraktion](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## Logische Operatoren  
  
|Beschreibung|Symbol|  
|------------------|------------|  
|[Logisches NOT](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[Kleiner als](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Größer als](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[Kleiner oder gleich](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[Größer oder gleich](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[Gleichheit](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[Ungleichheit](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[Logisches AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[Logisches OR](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Bedingt \(ternär\)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Komma](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Strikte Gleichheit](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[Strikte Ungleichheit](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## Bitweise Operatoren  
  
|Beschreibung|Symbol|  
|------------------|------------|  
|[Bitweises NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Bitweises Linksschieben](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[Bitweises Rechtsschieben](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[Rechtsschieben ohne Vorzeichen](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[Bitweises AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Bitweises XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Bitweises OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## Zuweisungsoperatoren  
  
|Beschreibung|Symbol|  
|------------------|------------|  
|[Zuweisung](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[Verbundzuweisung](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\= \(wie \+\= und &\=\)|  
  
## Verschiedene Operatoren  
  
|Beschreibung|Symbol|  
|------------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|delete|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## Gleichheit und strikte Gleichheit \(Identität\)  
 Der Unterschied zwischen \=\= \(Gleich\) und \(\=\=\= strikte Gleichheit\) ist, dass der Gleichheitsoperator Werte verschiedener Typen umwandelt, bevor er auf Gleichheit überprüft.  Beispielsweise ergibt der Vergleich der Zeichenfolge "1" mit der Zahl 1 das Ergebnis "true".  Der strikte Gleichheitsoperator hingegen wandelt Werte unterschiedlichen Typs nicht um, und daher ergibt der Vergleich der Zeichenfolge "1" mit der Zahl 1 hier nicht "true".  
  
 Primitive Zeichenfolgen, Zahlen und boolesche Werte werden auf der Grundlage ihres Werts verglichen.  Wenn sie denselben Wert haben, sind sie gleich.  Objekte \(einschließlich der Objekte vom Typ `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` und `RegExp`\) werden anhand eines Verweises verglichen.  Selbst wenn zwei Objektvariablen dieser Typen den gleichen Wert haben, sind sie nur dann gleich, wenn sie auf exakt dasselbe Objekt verweisen.  
  
 Beispiel:  
  
```javascript  
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