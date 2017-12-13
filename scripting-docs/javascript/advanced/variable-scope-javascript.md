---
title: Variablenbereich (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="variable-scope-javascript"></a>Variablenbereich (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] umfasst zwei Bereiche: global und lokal. Eine außerhalb einer Funktionsdefinition deklarierte Variable ist eine globale Variable, und ihr Wert kann im gesamten Programm abgerufen und verändert werden. Eine innerhalb einer Funktionsdefinition deklarierte Variable ist eine lokale Variable. Sie wird bei jeder Ausführung der Funktion erstellt und anschließend zerstört. Ein Zugriff auf die Variable von irgendwelchem Code außerhalb der Funktion ist nicht möglich. JavaScript unterstützt keinen Blockbereich (bei dem geschweifte Klammern `{. . .}` einen neuen Bereich definieren), außer im Sonderfall von Blockbereichsvariablen.  
  
## <a name="scope-in-javascript"></a>Geltungsbereich in JavaScript  
 Eine lokale Variable kann denselben Namen wie eine globale Variable haben, ist von dieser jedoch völlig unabhängig. Eine Wertänderung in einer Variablen hat keinen Einfluss auf die andere. Innerhalb der Funktion, in der die lokale Variable deklariert wurde, hat nur diese Version eine Bedeutung.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 In JavaScript werden Variablen so ausgewertet, als wären sie am Anfang des Bereichs, in dem sie vorhanden sind, deklariert worden. Dies kann manchmal zu unerwartetem Verhalten führen, wie hier gezeigt wird.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] eine Funktion ausführt, wird zuerst nach allen Variablendeklarationen gesucht, beispielsweise nach `var someVariable;`. Variablen werden mit dem Anfangswert `undefined` erstellt. Auch wenn eine Variable mit einem Anfangswert deklariert wird, z. B. `var someVariable = "something";`, hat sie zuerst den Wert `undefined`, und sie nimmt nur dann den deklarierten Wert an, wenn die Zeile, die die Deklaration enthält, ausgeführt wird.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verarbeitet alle Variablendeklarationen, bevor Code ausgeführt wird. Daher spielt es keine Rolle, ob sich die Deklaration innerhalb eines bedingten Blocks oder eines anderen Konstrukts befindet. Sobald [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] alle Variablen gefunden hat, wird der Code in der Funktion ausgeführt. Wenn eine Variable implizit innerhalb einer Funktion deklariert wird (d. h. wenn sie auf der linken Seite eines Zuweisungsausdrucks steht, aber nicht mit `var` deklariert worden ist), dann wird sie als globale Variable erstellt.  
  
 In JavaScript speichert eine interne (geschachtelte) Funktion Verweise auf die lokalen Variablen, die im selben Bereich wie die Funktion selbst vorhanden sind, auch nachdem die Funktion zurückgibt. Dieser Satz von Verweisen wird als Abschluss bezeichnet. Im folgenden Beispiel gibt der zweite Aufruf zur inneren Funktion dieselbe Meldung ("Hello Bill") aus, wie der erste Aufruf, da der Eingabeparameter für die äußere Funktion, `name`, eine lokale Variable ist, die im Abschluss für die innere Funktion gespeichert wird.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>blockbezogene Variablen  
 Internet Explorer 11 stellt die Unterstützung von [let](../../javascript/reference/let-statement-javascript.md) und [const](../../javascript/reference/const-statement-javascript.md) bereit, die blockbezogene Variablen sind. Für diese Variablen definieren die geschweiften Klammern `{. . .}` einen neuen Geltungsbereich. Wenn Sie eine dieser Variablen auf einen bestimmten Wert festlegen, gilt der Wert nur für den Bereich, in dem er festgelegt wird.  
  
 Das folgende Beispiel veranschaulicht die Verwendung von `let` und der Blockbereichsdefinition.  
  
> [!NOTE]
>  Der folgende Code wird im Standardmodus von Internet Explorer 11 und höher unterstützt.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```