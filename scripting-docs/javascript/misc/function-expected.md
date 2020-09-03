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
ms.openlocfilehash: f177bf81a43c45dcff4cef3040c64425ed544057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816968"
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
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)