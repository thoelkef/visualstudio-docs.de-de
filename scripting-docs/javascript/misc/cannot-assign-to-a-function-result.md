---
title: Kann nicht zu einem Funktionsergebnis zuweisen | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a29c3f20392dc216c0306137c0dec6b22aaa58a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093860"
---
# <a name="cannot-assign-to-a-function-result"></a>Zuweisen zu einem Funktionsergebnis nicht möglich
Sie haben versucht, einen Wert zu einem Funktionsergebnis zuzuweisen. Das Ergebnis einer Funktion einer Variablen zugewiesen werden kann, aber es kann nicht als Variable verwendet werden. Wenn Sie einen neuen Wert für die Funktion selbst zuweisen möchten, lassen Sie die Klammern (den Funktionsaufruf-Operator). Das folgende Beispiel zeigt eine Situation, in der dieser Fehler generiert wird.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden Sie den Wert des Ergebnisses eines Funktionsaufrufs nicht etwa Sie können *zuweisen*. Sie können das Ergebnis des Funktionsaufrufs zuweisen *auf eine Variable* jedoch.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Alternativ können Sie der Funktion selbst (und nicht den Rückgabewert) einer Variablen zuweisen.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)