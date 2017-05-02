---
title: "break-Anweisung (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break-Anweisung"
  - "do...while-Anweisung"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break-Anweisung (JavaScript)
Beendet die aktuelle Schleife oder in Verbindung mit einer Bezeichnung `label` die zugehörige Anweisung.  
  
## Syntax  
  
```  
break [label];  
```  
  
## Hinweise  
 Das optionale `label`\-Argument gibt die Bezeichnung der Anweisung an, die unterbrochen wird.  
  
 In der Regel wird die `break`\-Anweisung in `switch`\-Anweisungen und in `while`, `for`, `for...in`\-Schleifen oder `do...while`\-Schleifen verwendet.  Meistens wird das `label`\-Argument in `switch`\-Anweisungen verwendet. Es kann jedoch in beliebigen Anweisungen verwendet werden, unabhängig davon, ob es sich um einfache oder um zusammengesetzte Anweisungen handelt.  
  
 Durch die Ausführung der `break`\-Anweisung wird die aktuelle Schleife oder Anweisung beendet und die Skriptausführung mit der unmittelbar nachfolgenden Anweisung begonnen.  
  
## Beispiele  
 In diesem Beispiel wird der Zähler zum Zählen von 1 bis 99 konfiguriert. Die `break`\-Anweisung beendet die Schleife jedoch nach 14 Durchläufen.  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Im folgenden Code verweist die `break`\-Anweisung auf die `for`\-Schleife, der die `Inner:`\-Anweisung vorangestellt ist.  Wenn `j` gleich 24 ist, führt die `break` \-Anweisung dazu, dass der Programmfluss diese Schleife verlässt.  Die Zahlen 21 bis 23 werden auf jeder Zeile gedruckt.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [continue\-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [do...while\-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Anweisung mit Marke](../../javascript/reference/labeled-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)