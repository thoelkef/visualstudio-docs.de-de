---
title: '&#39;zurückgeben&#39; Anweisung ist außerhalb der Funktion | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846517"
---
# <a name="39return39-statement-outside-of-function"></a>&#39;zurückgeben&#39; Anweisung ist außerhalb der Funktion
Sie verwendet eine `return` -Anweisung in den globalen Bereich Ihres Codes. Die `return` Anweisung sollte nur im Text einer Funktion verwendet werden.  
  
 Aufrufen einer Funktion mit dem `()` Operator ist ein Ausdruck. Alle Ausdrücke über Werte verfügen; die `return` Anweisung dient zum Angeben des Werts von einer Funktion zurückgegeben. Das allgemeine Format lautet:  
  
```  
  
return [ expression ];  
```  
  
 Wenn die `return` -Anweisung wird ausgeführt, *Ausdruck* ausgewertet und als Wert für die Funktion zurückgegeben. Es ist kein Ausdruck **undefiniert** zurückgegeben wird.  
  
 Die Ausführung der Funktion angehalten, sobald die `return` -Anweisung ausgeführt wird, auch wenn Sie weitere Anweisungen im Hauptteil Funktion noch vorhanden sind. Die Ausnahme von dieser Regel wird Wenn die **zurückgeben** -Anweisung befindet sich in eine **versuchen Sie es** Block, und gibt es eine entsprechende **schließlich** -block, den Code in die  **zum Schluss** Block wird ausgeführt, bevor die Funktion zurückgibt.  
  
 Eine Funktion zurück, da das Ende des Funktionstexts ohne Ausführung erreicht eine `return` -Anweisung zurückgegebene Wert ist die **undefiniert** Wert (Dies bedeutet, dass das Ergebnis der Funktion kann nicht als Teil eines umfangreicheren Ausdrucks verwendet werden ).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `return` Anweisung vom Hauptteil des Codes (Globaler Gültigkeitsbereich).  
  
## <a name="see-also"></a>Siehe auch  
 [return Statement („return“-Anweisung)](../../javascript/reference/return-statement-javascript.md)   
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [caller-Eigenschaft (Funktion)](../../javascript/reference/caller-property-function-javascript.md)