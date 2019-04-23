---
title: Kann nicht zu einem Funktionsergebnis zuweisen | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226056f139e45f432d757aff8f8774b013742de3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076811"
---
# <a name="cannot-assign-to-a-function-result"></a>Zuweisen zu einem Funktionsergebnis nicht möglich
Sie haben versucht, einen Wert zu einem Funktionsergebnis zuzuweisen. Das Ergebnis einer Funktion einer Variablen zugewiesen werden kann, aber es kann nicht als Variable verwendet werden. Wenn Sie einen neuen Wert für die Funktion selbst zuweisen möchten, lassen Sie die Klammern (den Funktionsaufruf-Operator). Das folgende Beispiel zeigt eine Situation, in der dieser Fehler generiert wird.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Verwenden Sie den Wert des Ergebnisses eines Funktionsaufrufs nicht etwa Sie können *zuweisen*. Sie können das Ergebnis des Funktionsaufrufs zuweisen *auf eine Variable* jedoch.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternativ können Sie der Funktion selbst (und nicht den Rückgabewert) einer Variablen zuweisen.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)