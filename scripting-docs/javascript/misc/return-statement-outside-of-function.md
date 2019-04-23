---
title: "\"return\"-Anweisung ist außerhalb der Funktion | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01ef96385d5fe3dccf14a7491e67983d39913280
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100390"
---
# <a name="return-statement-outside-of-function"></a>return-Anweisung ist außerhalb der Funktion
Sie verwendet eine `return` -Anweisung in den globalen Bereich Ihres Codes. Die `return` Anweisung sollte nur im Text einer Funktion verwendet werden.  
  
 Aufrufen einer Funktion mit dem `()` Operator ist ein Ausdruck. Alle Ausdrücke über Werte verfügen; die `return` Anweisung dient zum Angeben des Werts von einer Funktion zurückgegeben. Das allgemeine Format lautet:  
  
```js
  
return [ expression ];  
```  
  
 Wenn die `return` -Anweisung wird ausgeführt, *Ausdruck* ausgewertet und als Wert für die Funktion zurückgegeben. Es ist kein Ausdruck **undefiniert** zurückgegeben wird.  
  
 Die Ausführung der Funktion angehalten, sobald die `return` -Anweisung ausgeführt wird, auch wenn Sie weitere Anweisungen im Hauptteil Funktion noch vorhanden sind. Die Ausnahme von dieser Regel wird Wenn die **zurückgeben** -Anweisung befindet sich in eine **versuchen Sie es** Block, und gibt es eine entsprechende **schließlich** -block, den Code in die  **zum Schluss** Block wird ausgeführt, bevor die Funktion zurückgibt.  
  
 Eine Funktion zurück, da das Ende des Funktionstexts ohne Ausführung erreicht eine `return` -Anweisung zurückgegebene Wert ist die **undefiniert** Wert (Dies bedeutet, dass das Ergebnis der Funktion kann nicht als Teil eines umfangreicheren Ausdrucks verwendet werden ).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie die `return` Anweisung vom Hauptteil des Codes (Globaler Gültigkeitsbereich).  
  
## <a name="see-also"></a>Siehe auch  
 [return Statement („return“-Anweisung)](../../javascript/reference/return-statement-javascript.md)   
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [caller-Eigenschaft (Funktion)](../../javascript/reference/caller-property-function-javascript.md)