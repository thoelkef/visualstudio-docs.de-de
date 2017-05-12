---
title: "Rekursion (JavaScript) | Microsoft Docs"
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
  - "Funktionen, Rekursive Funktionsaufrufe"
  - "Rekursive Prozeduren"
  - "Funktionsaufrufe, Rekursive"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Rekursion (JavaScript)
Rekursion ist eine wichtige Programmiertechnik, bei der eine Funktion sich selbst aufruft.  
  
## Beispiel für die Rekursion  
 Ein Beispiel ist die Berechnung von Fakultäten.  Die Fakultät einer Zahl *n* wird durch 1 \* 2 \* 3 \*...  *n* berechnet.  Im folgenden Beispiel wird gezeigt, wie Fakultäten iterativ ermittelt werden, d. h. mit einer `while`\-Schleife, in der das Ergebnis berechnet wird.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Sie können das Beispiel rekursiv sehr vereinfachen.  Anstatt eine `while`\-Schleife zu verwenden, um den Wert zu berechnen, können Sie `factorial` einfach erneut aufrufen und dabei den nächsten kleinsten Wert übergeben.  Die Rekursion wird beendet, wenn der Wert 1 ist.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```