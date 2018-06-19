---
title: Rekursion (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- functions, recursive function calls
- recursive procedures
- function calls, recursive
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06735c244ed6bd3c8d9abe59123f9f961e6f1847
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568890"
---
# <a name="recursion-javascript"></a>Rekursion (JavaScript)
Rekursion ist eine wichtige Programmiertechnik, in der eine Funktion sich selbst aufruft.  
  
## <a name="an-example-of-recursion"></a>Ein Beispiel der Rekursion  
 Ein Beispiel ist die Berechnung von Fakultäten. Die Fakultät einer Zahl  *n* wird durch Multiplikation von 1 \* 2 \* 3 \*... *n* berechnet. Das folgende Beispiel zeigt, wie Fakultäten iterativ berechnet werden, d.h. durch Benutzen einer `while`-Schleife, in der das Ergebnis berechnet wird.  
  
```JavaScript  
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
  
 Sie können das Beispiel sehr einfach rekursiv machen. Anstatt eine `while`-Schleife zum Berechnen des Werts zu verwenden, können Sie einfach erneut `factorial` aufrufen, wobei der nächst niedrigere Wert übergeben wird. Die Rekursion endet, wenn der Wert 1 ist.  
  
```JavaScript  
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