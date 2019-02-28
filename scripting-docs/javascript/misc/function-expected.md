---
title: Funktion erwartet. | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 41d1ecc982dcdc4d494fc167e4784e9121bec15e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843934"
---
# <a name="function-expected"></a>Funktion erwartet
Entweder Sie haben versucht, zum Aufrufen einer der **Funktionsprototyp** Methoden für ein Objekt, das nicht war eine `Function` -Objekt, oder Sie ein Objekt im Kontext eines Funktionsaufrufs verwendet. Der folgende Code erzeugt z. B. diesen Fehler, da **Beispiel** ist keine Funktion.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur **Funktionsprototyp** Methoden `Function` Objekte.  
  
-   Stellen Sie sicher, dass Sie den Funktionsaufruf-Operator verwenden `()` nur Funktionen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)