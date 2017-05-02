---
title: "for-Anweisung (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Schleifenstruktur, for-Anweisungen"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for-Anweisung (JavaScript)
Führt einen Anweisungsblock aus, solange eine angegebene Bedingung "true" ist.  
  
## Syntax  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## Parameter  
 `initialization`  
 Optional.  Ein Ausdruck.  Dieser Ausdruck wird nur einmal vor der Ausführung der Schleife ausgeführt.  
  
 `test`  
 Optional.  Ein boolescher Ausdruck.  Wenn `test` `true` ist, wird `statement` ausgeführt.  Wenn `test` `false` ist, wird die Schleife beendet.  
  
 `increment`  
 Optional.  Ein Ausdruck.  Nach jedem Schleifendurchlauf wird der Inkrementausdruck ausgeführt.  
  
 `statement`  
 Optional.  Eine oder mehrere Anweisungen, die ausgeführt werden sollen, wenn `test` **true** ist.  Hierbei kann es sich um eine Verbundanweisung handeln.  
  
## Hinweise  
 In der Regel werden `for` verwendet, wenn die Anzahl der Schleifeniterationen feststeht.  Die `for`\-Schleife eignet sich zum Durchlaufen von Arrays und für die sequenzielle Verarbeitung.  
  
 Da der Test des bedingten Ausdrucks vor dem Ausführen der Schleife erfolgt, wird eine `for`\-Anweisung null Mal, einmal oder häufiger ausgeführt.  
  
 Auf jeder Zeile im Anweisungsblock einer `for`\-Schleife können Sie diese mithilfe der `break`\-Anweisung beenden, Sie können aber auch die `continue`\-Anweisung verwenden, um die Steuerung an die nächste Iteration der Schleife zu übertragen.  
  
## Beispiel  
 Im folgenden Beispiel werden mit der `for`\-Anweisung die eingeschlossenen Anweisungen wie folgt ausgeführt:  
  
-   Zuerst wird der Anfangswert der Variablen `i` ausgewertet.  
  
-   Sofern der Wert von `i` kleiner oder gleich 9 ist, werden die `document.write`\-Anweisungen ausgeführt, und `i` wird erneut ausgewertet.  
  
-   Wenn `i` größer als 9 ist, ergibt die Auswertung der Bedingung "false", und die Steuerung wird von der Schleife abgegeben.  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## Beispiel  
 Alle Ausdrücke der `for`\-Anweisung sind optional.  Im folgenden Beispiel implementieren die `for`\-Anweisungen eine Endlosschleife, und die Schleife wird mit einer `break`\-Anweisung beendet.  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)