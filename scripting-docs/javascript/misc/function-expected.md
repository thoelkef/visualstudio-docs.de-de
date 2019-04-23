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
ms.openlocfilehash: 4442143b2766ed3608a852d0f811a6b943fd19df
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117049"
---
# <a name="function-expected"></a>Funktion erwartet
Entweder Sie haben versucht, zum Aufrufen einer der **Funktionsprototyp** Methoden für ein Objekt, das nicht war eine `Function` -Objekt, oder Sie ein Objekt im Kontext eines Funktionsaufrufs verwendet. Der folgende Code erzeugt z. B. diesen Fehler, da **Beispiel** ist keine Funktion.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur **Funktionsprototyp** Methoden `Function` Objekte.  
  
- Stellen Sie sicher, dass Sie den Funktionsaufruf-Operator verwenden `()` nur Funktionen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)