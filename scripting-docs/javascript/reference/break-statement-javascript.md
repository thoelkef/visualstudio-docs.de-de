---
title: break-Anweisung (JavaScript) | Microsoft Docs
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
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634150"
---
# <a name="break-statement-javascript"></a>break-Anweisung (JavaScript)
Beendet die aktuelle Schleife oder in Verbindung mit einer `label`, die zugehörige Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale `label` Argument gibt die Bezeichnung der Anweisung, die Sie über wichtige sind.  
  
 In der Regel die `break` -Anweisung in `switch` Anweisungen und `while`, `for`, `for...in`, oder `do...while` Schleifen. Sie am häufigsten verwenden die `label` Argument in `switch` -Anweisungen, aber sie können verwendet werden in jeder Anweisung ob einfach oder zusammengesetzten.  
  
 Ausführen der `break` -Anweisung beendet die aktuelle Schleife oder Anweisung und Ausführen von Skripts mit der Anweisung unmittelbar nach beginnt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird der Leistungsindikator einrichten, von 1 bis 99 zählen; allerdings die `break` -Anweisung beendet die Schleife nach 14 Anzahlen.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Im folgenden Code wird die `break` Anweisung verweist auf die `for` Schleife, in der vorangestellt ist die `Inner:` Anweisung. Wenn `j` 24, entspricht die `break` Anweisung veranlasst den Programmfluss, um diese Schleife zu beenden. Die Zahlen 21 bis 23, die auf jeder Zeile ausgegeben werden.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [continue-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [Do...While-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for... in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Anweisung mit Bezeichnung](../../javascript/reference/labeled-statement-javascript.md)   
 [while-Anweisung](../../javascript/reference/while-statement-javascript.md)