---
title: Funktion erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2028d8923c2f81d1d99fec752d7ac0ce2fb32f65
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862170"
---
# <a name="function-expected"></a>Funktion erwartet
Entweder haben Sie versucht, eine der **Funktionsprototyp** -Methoden für ein Objekt aufzurufen, das kein- `Function` Objekt war, oder Sie haben ein Objekt in einem Funktionsaufruf Kontext verwendet. Der folgende Code erzeugt z. b. diesen Fehler, da **example** keine Funktion ist.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Ruft nur **Funktionsprototyp** -Methoden für- `Function` Objekte auf.  
  
- Stellen Sie sicher, dass Sie den Funktions Aufrufoperator verwenden `()` , um nur Funktionen aufzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Function-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype-Eigenschaft (Objekt)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)