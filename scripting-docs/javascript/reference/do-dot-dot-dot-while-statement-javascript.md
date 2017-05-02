---
title: "do...while-Anweisung (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while-Anweisung"
  - "Terminieren von Schleifen"
  - "Schleifenstrukturen, „do“ und „do-while“"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while-Anweisung (JavaScript)
Führt einen Anweisungsblock einmal aus und wiederholt dann die Ausführung der Schleife, bis ein bedingter Ausdruck mit `false` ausgewertet wird.  
  
## Syntax  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Parameter  
 `statement`  
 Erforderlich.  Die auszuführende Anweisung, wenn `expression` den Wert `true` hat.  Hierbei kann es sich um eine zusammengesetzte Anweisung handeln.  
  
 `expression`  
 Erforderlich.  Ein Ausdruck, der in den booleschen Wert `true` oder `false` umgewandelt werden kann.  Wenn `expression` `true` ist, wird die Schleife erneut ausgeführt.  Wenn `expression` `false` ist, wird die Schleife beendet.  
  
## Hinweise  
 Im Gegensatz zur `while`\-Anweisung wird eine `do...while`\-Schleife einmal ausgeführt, bevor der bedingte Ausdruck ausgewertet wird.  
  
 Sie können auf jeder Zeile eines `do…while`\-Blocks die `break`\-Anweisung verwenden, wenn die Schleife im Programmablauf beendet werden soll, Sie können jedoch auch mit der `continue`\-Anweisung direkt zum `while`\-Ausdruck wechseln.  
  
## Beispiel  
 Im folgenden Beispiel werden die Anweisungen in der `do...while`\-Schleife so lange ausgeführt, solange die Variable `i` kleiner als 10 ist.  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## Beispiel  
 Im folgenden Beispiel werden die Anweisungen innerhalb der Schleife einmal ausgeführt, obwohl die Bedingung nicht erfüllt wird.  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue\-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)   
 [Anweisung mit Marke](../../javascript/reference/labeled-statement-javascript.md)