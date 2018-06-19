---
title: continue-Anweisung (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636380"
---
# <a name="continue-statement-javascript"></a>continue-Anweisung (JavaScript)
Beendet die aktuelle Iteration einer Schleife und beginnt eine neue Iteration.  
  
## <a name="syntax"></a>Syntax  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale `label` Argument gibt die Anweisung an die `continue` gilt.  
  
 Sie können die `continue` Anweisung nur innerhalb einer `while`, `do...while`, **für**, oder `for...in` Schleife. Ausführen der `continue` -Anweisung beendet die aktuelle Iteration der Schleife und Programmablauf mit dem Anfang der Schleife fortgesetzt. Dies hat folgenden Auswirkungen auf die verschiedenen Typen von Schleifen:  
  
-   `while`und `do...while` Schleifen, deren Bedingung testen und bei "true", die Schleife erneut ausgeführt.  
  
-   `for`Schleifen führen ihre Inkrementausdruck, und wenn der Testausdruck "true" wird die Schleife erneut ausgeführt.  
  
-   `for...in`Schleifen, fahren Sie mit der nächsten Feld der angegebenen Variablen und die Schleife erneut ausgeführt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel durchlaufen eine Schleife von 1 bis 9 aus. Die Anweisungen zwischen `continue` und das Ende der `for` Text werden ausgelassen, aufgrund der Verwendung von der `continue` Anweisung zusammen mit dem Ausdruck `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Im folgenden Code wird die `continue` Anweisung verweist auf die `for` Schleife, in der vorangestellt ist die `Inner:` Bezeichnung. Wenn `j` 24, ist die `continue` Anweisung verursacht, die `for` -Schleife zur nächsten Iteration wechseln. Die Zahlen 21 bis 23 und 25 bis 30 Drucken in jeder Zeile.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Do...While-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for... in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Anweisung mit Bezeichnung](../../javascript/reference/labeled-statement-javascript.md)   
 [while-Anweisung](../../javascript/reference/while-statement-javascript.md)