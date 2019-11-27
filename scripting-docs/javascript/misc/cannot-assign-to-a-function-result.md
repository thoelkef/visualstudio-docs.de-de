---
title: Zuweisen zu einem Funktionsergebnis nicht möglich | Microsoft-Dokumentation
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
ms.openlocfilehash: aca09fe3b516fbb8f27def982bf34a22d33d4ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572358"
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
  
## <a name="see-also"></a>Siehe auch  
 [Funktions Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)