---
title: "continue-Anweisung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue-Anweisung"
  - "do...while-Anweisung"
  - "Schleifenstruktur, continue-Anweisung"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue-Anweisung (JavaScript)
Beendet die aktuelle Iteration einer Schleife und beginnt eine neue Iteration.  
  
## Syntax  
  
```  
continue [label];  
```  
  
## Hinweise  
 Das optionale Argument `label` legt die Anweisung fest, für die `continue` gilt.  
  
 Sie können die Anweisung nur innerhalb einer `continue` statement only inside a `while`, `do...while`, **for** oder `for...in`\-Schleife verwenden.  Die Ausführung der `continue`\-Anweisung beendet die laufende Iteration und setzt den Programmablauf mit dem Beginn der nächsten Schleife fort.  Dies hat die folgenden Auswirkungen auf die verschiedenen Schleifenarten:  
  
-   Bei den Schleifen `while` und `do...while` wird die Bedingung überprüft. Ist diese "true", wird die Schleife erneut ausgeführt.  
  
-   Bei `for`\-Schleifen wird der Inkrementausdruck und, sofern der Testausdruck true ergibt, die Schleife erneut ausgeführt.  
  
-   `for...in`\-Schleifen springen zum nächsten Feld der angegebenen Variablen und führen die Schleife erneut aus.  
  
## Beispiele  
 In diesem Beispiel durchläuft eine Schleife den Bereich 1 bis 9.  Die Anweisungen zwischen `continue` und dem Ende des `for`\-Texts werden wegen der Verwendung der `continue`\-Anweisung zusammen mit dem Ausdruck `(i < 5)` übersprungen.  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Im folgenden Code verweist die `continue`\-Anweisung auf die `for`\-Schleife, der die `Inner:`\-Bezeichnung vorangestellt ist.  Wenn `j` gleich 24 ist, führt die `continue`\-Anweisung dazu, dass die `for`\-Schleife zur nächsten Iteration wechselt.  Die Zahlen 21 bis 23 und 25 bis 30 werden auf jeder Zeile ausgegeben.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [do...while\-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Anweisung mit Marke](../../javascript/reference/labeled-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)