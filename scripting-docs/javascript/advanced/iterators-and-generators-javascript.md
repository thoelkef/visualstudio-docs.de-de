---
title: "Iteratoren und Generatoren (JavaScript) | Microsoft Docs"
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
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Iteratoren und Generatoren (JavaScript)
Ein Iterator ist ein Objekt, das verwendet wird, um ein Containerobjekt wie eine Liste zu durchlaufen.  In JavaScript ist ein Iterator\-Objekt kein bestimmtes, integriertes Objekt, ist jedoch ein Objekt, das eine `next`Methode implementiert, um auf das nächste Element im Container\-Objekt zuzugreifen.  
  
 In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]können Sie Ihre eigenen benutzerdefinierten Iteratoren erstellen.  Es ist jedoch im Allgemeinen einfacher, Generatoren zu verwenden, die die Erstellung von Iteratoren erheblich vereinfachen.  Generatoren sind ein Funktionstyp, der als Factory für Iteratoren dient.  Weitere Informationen zum Erstellen eines benutzerdefinierten Iterators mithilfe einer Genratorfunktion finden Sie unter [Generatoren](#Generators).  
  
> [!CAUTION]
>  Generatoren werden in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
## Iteratoren  
 Zur Implementierung eines JavaScript\-Iterators gehören zwei oder drei Objekte, die bestimmten Schnittstellen entsprechen:  
  
-   Iterable\-Schnittstelle  
  
-   Iterator\-Schnittstelle  
  
-   IteratorResult\-Schnittstelle  
  
 Durch die Verwendung dieser Schnittstellen können Sie benutzerdefinierte Iteratoren erstellen.  Dadurch können Sie ein iterable\-Objekt mit der `for…of`Anweisung durchlaufen.  
  
### Iterable\-Schnittstelle  
 Die Iterable\-Schnittstelle ist die erforderliche Schnittstelle für ein iterable\-Objekt \(ein Objekt, für das ein Iterator abgerufen werden kann\).  Beispielsweise muss `C` in `for (let e of C)` die Iterable\-Schnittstelle implementieren.  
  
 Ein iterable\-Objekt muss die Symbol.iterator\-Methode bereitstellen, die einen Iterator zurückgibt.  
  
```javascript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Diese Eigenschaft muss eine Funktion sein, die keine Argumente akzeptiert und ein Objekt \(`iterObject`\) zurückgibt, dass der `Iterator`\-Schnittstelle entspricht.  
  
 Viele integrierte Typen, einschließlich Arrays, sind nun iterable.  Die `for…of`\-Schleife verarbeitet ein iterable\-Objekt.  \(Nicht alle integrierten iterables sind Iteratoren.  Ein Arrayobjekt ist beispielsweise selbst kein Iterator, ist jedoch iterable, ein ArrayIterator ist hingegen ebenfalls iterable\).  
  
### Iterator\-Schnittstelle  
 Das von der Symbol.iterator\-Methode zurückgegebene Objekt muss die `next`\-Methode implementieren.  Die `next`\-Methode weist folgende Syntax auf:  
  
```javascript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 Die `next`\-Methode ist eine Funktion, die einen Wert zurückgibt.  Die Funktion gibt ein Objekt \(`iterResultObj`\) zurück, das der `IteratorResult`\-Schnittstelle entspricht.  Wenn ein vorheriger Aufruf der `next`\-Methode eines Iterators ein `IteratorResult`\-Objekt zurückgibt, dessen `done`Eigenschaft true lautet, wird die Iteration beendet und die `next`\-Methode nicht erneut aufgerufen.  
  
 Iteratoren können auch eine `return`\-Methode umfassen, um sicherzustellen, dass der Iterator ordnungsgemäß freigegeben wird, wenn das Skript beendet wurde.  
  
### IteratorResult\-Schnittstelle  
 Die IteratorResult\-Schnittstelle ist die erforderliche Schnittstelle für das Ergebnis der `next` \-Methode für einen Iterator.  Das von der `next` zurückgegebene Objekt muss eine `done`\- und `value`\-Eigenschaft bereitstellen.  
  
```javascript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 Die `done`\-Eigenschaft gibt den Status des `next`\-Methodenaufrufs eines Iterators zurück, dieser lautet true oder false.  Wenn das Ende des Iterators erreicht wurde, gibt `done` true zurück.  Wenn das Ende nicht erreicht wurde, gibt `done` false zurück und ein Wert ist verfügbar.  Wenn die `done`Eigenschaft \(entweder seine eigene oder eine geerbte Eigenschaft\) nicht vorhanden ist, wird das Ergebnis der `done` als false behandelt.  
  
 Wenn `done` false lautet, gibt die `value`\-Eigenschaft den aktuellen Wert des Iteration\-Elements zurück.  Wenn `done` true ist, ist dies der Rückgabewert des Iterators, wenn ein Rückgabewert angegeben wird.  Wenn der Iterator keinen Rückgabewert besitzt, ist `value` nicht definiert.  In diesem Fall ist die `value`Eigenschaft im übereinstimmenden\-Objekt möglicherweise nicht vorhanden, wenn sie keine explizite Value\-Eigenschaft erbt.  
  
<a name="Generators"></a>   
## Generatoren  
 Erstellen Sie zum einfachen Erstellen und Verwenden von benutzerdefinierten Iteratoren eine Generatorfunktion, indem Sie die Funktionssyntax\* zusammen mit einem oder mehreren `yield` Ausdrücken verwenden.  Die Generatorfunktion gibt einen Iterator \(d. h. einen Generator\) zurück, über den der Generatorfunktionstext ausgefhrt wird.  Die Funktion wird bis zur nächsten `yield`\- oder `return`\-Anweisung ausgeführt.  
  
 Rufen Sie die `next`\-Methode des Iterators auf, um den nächsten Wert aus der Generatorfunktion zurückzugeben.  
  
 Das folgende Beispiel zeigt einen Generator, der für ein Zeichenfolgeobjekt einen Iterator zurückgibt.  
  
```javascript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 In einem Generator beendet der Yield\-Operand\-Ausdruck den Aufruf von `next` und gibt ein `IteratorResult`\-Objekt mit zwei Eigenschaften zurück: `done` \(`done=false`\) und `value` \(`value=operand`\).  `operand` ist optional, und wenn der Wert nicht vorhanden bleibt, dann ist der Wert nicht definiert.  
  
 In einem Generator beendet eine `return`\-Anweisung den Generator, indem er eine `IteratorResult` mit `done=true` und dem optionalen Operand\-Ergebnis für die Value\-Eigenschaft zurückgibt.  
  
 Können Sie auch einen `yield*`\-Ausdruck anstelle von `yield` verwenden, um beispielweise ein Array oder eine Zeichenfolge an einen anderen Generator oder ein anderes iterable\-Objekt zu delegieren.  
  
 Wenn Sie den folgenden Code im vorhergehenden Beispiel anhängen, delegiert `yield*` an den `stringIter`\-Generator.  
  
```javascript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 Sie können auch erweiterte Generatoren erstellen, indem Sie ein Argument an `next` übergeben und das Argument zum Ändern des Status des Generators zu verwenden.  `next` wird der Ergebniswert des zuvor ausgeführten `yield`\-Ausdrucks.  Im folgenden Beispiel wird bei der Übergabe eines Werts von 100 an die `next`\-Methode der interne Indexwert des Generators zurückgesetzt.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }  
  
var si3 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 Andere erweiterte Generatoren können die `throw`\-Methode des Generators aufrufen.  Der ausgelöste Fehler wird angezeigt, damit er bei angehaltenem Generator abgerufen werden kann \(vor der nächsten `yield`Anweisung\).