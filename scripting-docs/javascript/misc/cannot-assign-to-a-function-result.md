---
title: Zuweisen zu einem Funktionsergebnis nicht möglich | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817631"
---
# <a name="cannot-assign-to-a-function-result"></a>Zuweisen zu einem Funktionsergebnis nicht möglich
Sie haben versucht, einem Funktionsergebnis einen Wert zuzuweisen. Das Ergebnis einer Funktion kann einer Variablen zugewiesen werden, Sie kann jedoch nicht als Variable verwendet werden. Wenn Sie der Funktion selbst einen neuen Wert zuweisen möchten, lassen Sie die Klammern aus (der Funktions Aufrufoperator). Das folgende Beispiel zeigt eine Situation, in der dieser Fehler generiert wird.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Verwenden Sie nicht den Wert eines Funktions aufrufergebnisses als etwas, das Sie *zuweisen*können. Sie können das Ergebnis des Funktions Aufrufes jedoch auch *einer Variablen* zuweisen.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternativ können Sie die Funktion selbst (und nicht deren Rückgabewert) einer Variablen zuweisen.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)