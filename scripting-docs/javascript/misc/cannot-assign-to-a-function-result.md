---
title: Kann nicht zu einem Funktionsergebnis zuweisen | Microsoft Docs
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
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632980"
---
# <a name="cannot-assign-to-a-function-result"></a>Zuweisen zu einem Funktionsergebnis nicht möglich
Sie haben versucht, einen Wert zu einem Funktionsergebnis zuzuweisen. Das Ergebnis einer Funktion einer Variablen zugewiesen werden kann, aber er kann als eine Variable verwendet werden. Wenn Sie einen neuen Wert für die Funktion selbst zuweisen möchten, lassen Sie die Klammern (den Funktionsaufrufoperator). Das folgende Beispiel zeigt eine Situation, in der dieser Fehler generiert wird.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden Sie den Wert des Ergebnisses eines Funktionsaufrufs nicht als ein Element Sie können *zuweisen*. Sie können das Ergebnis des Funktionsaufrufs zuweisen *einer Variablen* Obwohl.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Alternativ können Sie der Funktion selbst (und nicht dessen Rückgabewert) einer Variablen zuweisen.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)