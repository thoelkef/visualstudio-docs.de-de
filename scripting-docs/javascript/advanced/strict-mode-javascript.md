---
title: Strict-Modus (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="strict-mode-javascript"></a>Strict-Modus (JavaScript)
Der Strict-Modus ermöglicht eine bessere Fehlerüberprüfung innerhalb des Codes. Beispielsweise ist es im Strict-Modus nicht möglich, implizit deklarierte Variablen zu verwenden, schreibgeschützten Eigenschaften Werte zuzuweisen oder nicht erweiterbaren Objekten Eigenschaften hinzuzufügen. Die Einschränkungen werden im Abschnitt [Einschränkungen für Code im Strict-Modus](../../javascript/advanced/strict-mode-javascript.md#rest) weiter unten in diesem Thema aufgeführt. Weitere Informationen über den Strict-Modus finden Sie unter [ECMAScript-Sprachenspezifikation, 5. Edition](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  Der Strict-Modus wird erst ab Internet Explorer 10 unterstützt.  
  
## <a name="declaring-strict-mode"></a>Deklarieren des Strict-Modus  
 Sie können den Strict-Modus deklarieren, indem Sie am Anfang einer Datei, eines Programms oder einer Funktion `"use strict";` hinzufügen. Diese Art der Deklaration wird als *Anweisungseinleitung* bezeichnet. Der Bereich einer Strict-Modus-Deklaration ist vom Kontext abhängig. Wird die Deklaration in einem globalen Kontext (nicht im Bereich einer Funktion) erstellt, gilt der Strict-Modus für den gesamten Programmcode. Bei einer Deklaration innerhalb einer Funktion ist der Strict-Modus für den gesamten Code der Funktion gültig. Im folgenden Beispiel gilt der Strict-Modus für den gesamten Code. Da die Variablendeklaration außerhalb der Funktion liegt, wird der Syntaxfehler "Nicht definierte Variable im Strict-Modus" ausgelöst.  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 Im folgenden Beispiel gilt der Strict-Modus nur für den Code in der `testFunction`. Der Syntaxfehler wird nicht von der Variablendeklaration außerhalb der Funktion verursacht, sondern von der Deklaration innerhalb der Funktion.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Einschränkungen für Code im Strict-Modus  
 In der folgenden Tabelle sind die wichtigsten Einschränkungen für den Strict-Modus aufgeführt.  
  
|||||  
|-|-|-|-|  
|**Sprachelement**|**Einschränkung**|**Fehler**|**Beispiel**|  
|Variable|Verwenden einer Variable, die nicht deklariert ist.|SCRIPT5042: Variable im Strict-Modus undefiniert|`testvar = 4;`|  
|Schreibgeschützte Eigenschaft|Schreiben in eine schreibgeschützte Eigenschaft.|SCRIPT5045: Im Strict-Modus sind Zuweisungen an schreibgeschützte Eigenschaften nicht zulässig.|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Nicht erweiterbare Eigenschaft|Hinzufügen einer Eigenschaft zu einem Objekt, dessen `extensible`-Attribut auf `false` festgelegt ist.|SCRIPT5046: Die Eigenschaft für ein nicht erweiterbares Objekt kann nicht erstellt werden.|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Löschen einer Variable, einer Funktion oder eines Arguments.<br /><br /> Löschen einer Eigenschaft, deren `configurable`-Attribut auf `false` festgelegt ist.|SCRIPT1045: Das Aufrufen von „delete“ für einen \<Ausdruck> ist im Strict-Modus nicht zulässig.|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplizieren einer Eigenschaft|Mehrfachdefinition einer Eigenschaft im selben Objektliteral.|SCRIPT1046: Mehrere Definitionen einer Eigenschaft sind im Strict-Modus nicht zulässig|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplizieren eines Parameternamens|Mehrfachverwendung eines Parameternamens in einer Funktion.|SCRIPT1038: Doppelte formale Parameternamen sind im Strict-Modus nicht zulässig|`function testFunc(param1, param1) {     return 1; };`|  
|Für die zukünftige Verwendung reservierte Schlüsselwörter|Verwenden eines für die zukünftige Verwendung reservierten Schlüsselworts als Variablen- oder Funktionsname.|SCRIPT1050: Das Verwenden eines für die zukünftige Verwendung reservierten Worts für einen Bezeichner ist ungültig. Der Bezeichnername ist im strict-Modus reserviert.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Oktale|Zuweisen eines Oktalwerts zu einem numerischen Literal oder der Versuch der Verwendung eines Escapezeichens für einen Oktalwert.|SCRIPT1039: Numerische Oktalliterale und Escapezeichen sind im Strict-Modus nicht zulässig.|`var testoctal = 010; var testescape = \010;`|  
|`this`|Der Wert von `this` wird nicht in das globale Objekt konvertiert, wenn er `null` oder `undefined` lautet.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> Außerhalb des Strict-Modus ist der Wert von `testvar` das globale Objekt, während der Wert im Strict-Modus `undefined` ist.|  
|`eval` als Bezeichner|Die Zeichenfolge "eval" kann nicht als Bezeichner (Variablen- oder Funktionsname, Parametername, usw.) verwendet werden.||`var eval = 10;`|  
|Funktionsdeklaration innerhalb einer Anweisung oder eines Blocks|Eine Funktion kann nicht innerhalb einer Anweisung oder eines Blocks deklariert werden.|SCRIPT1047: Im Strict-Modus können Funktionsdeklarationen nicht in einer Anweisung oder einem Block geschachtelt werden. Sie dürfen nur auf oberster Ebene oder direkt in einem Funktionstext vorkommen.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Variablendeklaration innerhalb einer `eval`-Funktion|Eine Variable, die innerhalb einer `eval`-Funktion deklariert wurde, kann nicht außerhalb dieser Funktion verwendet werden.|SCRIPT1041: Ungültige Verwendung von "eval" im Strict-Modus|`eval("var testvar = 10"); testvar = 15;`<br /><br /> Indirekte Auswertung ist möglich, aber eine Variable, die außerhalb der `eval`-Funktion deklariert wurde, kann trotzdem nicht verwendet werden.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Dieser Code verursacht den Fehler SCRIPT5009: 'testVar' ist nicht definiert.|  
|`Arguments` als Bezeichner|Die Zeichenfolge "arguments" kann nicht als Bezeichner (Variablen- oder Funktionsname, Parametername, usw.) verwendet werden.|SCRIPT1042: Ungültige Verwendung von "arguments" im Strict-Modus|`var arguments = 10;`|  
|`arguments` innerhalb einer Funktion|Die Werte von Membern des lokalen `arguments`-Objekts können nicht geändert werden.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> Außerhalb des Strict-Modus kann der Wert des Parameters `oneArg` geändert werden, indem der Wert von `arguments[0]` so angegeben wird, dass der Wert von `oneArg` und `arguments[0]` 20 lautet. Im Strict-Modus hat das Ändern des Werts von `arguments[0]` keine Auswirkung auf den Wert von `oneArg`, da es sich beim `arguments`-Objekt lediglich um eine lokale Kopie handelt.|  
|`arguments.callee`|Nicht zulässig.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Nicht zulässig.|SCRIPT1037: "with"-Anweisungen sind im Strict-Modus nicht zulässig|`with (Math){     x = cos(3);     y = tan(7); }`|
