---
title: "&#39; Return &#39; Anweisung ist außerhalb der Funktion | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; Return &#39; Anweisung ist außerhalb der Funktion
Sie verwendet ein `return` Anweisung im globalen Gültigkeitsbereich des Codes. Die `return` Anweisung sollte nur innerhalb des Texts einer Funktion angezeigt werden.  
  
 Aufrufen einer Funktion mit dem `()` Operator ist ein Ausdruck. Alle Ausdrücke über Werte verfügen; die `return` Anweisung dient zum Angeben des Werts von einer Funktion zurückgegeben. Das allgemeine Format ist:  
  
```  
  
return [ expression ];  
```  
  
 Wenn die `return` -Anweisung wird ausgeführt, *Ausdruck* ausgewertet und als Wert der Funktion zurückgegeben wird. Wenn es kein Ausdruck ist **undefined** zurückgegeben wird.  
  
 Die Ausführung der Funktion beendet wird, wenn die `return` -Anweisung ausgeführt wird, auch wenn andere Anweisungen im Hauptteil Funktion noch vorhanden sind. Die Ausnahme von dieser Regel wird Wenn die **zurückgeben** -Anweisung tritt innerhalb einer **versuchen Sie es** Block, und es wird eine entsprechende **schließlich** -Block den Code in der  **Schließlich** Block wird ausgeführt, bevor die Funktion beendet.  
  
 Eine Funktion zurück, da das Ende des Funktionstexts ohne Ausführung erreicht eine `return` -Anweisung zurückgegebene Wert ist die **undefined** Wert (Dies bedeutet, dass das Ergebnis der Funktion nicht als Teil eines umfangreicheren Ausdrucks verwendet werden ).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `return` -Anweisung aus dem Hauptteil des Codes (Globaler Gültigkeitsbereich).  
  
## <a name="see-also"></a>Siehe auch  
 [return Statement („return“-Anweisung)](../../javascript/reference/return-statement-javascript.md)   
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [caller-Eigenschaft (Funktion)](../../javascript/reference/caller-property-function-javascript.md)