---
title: Zirkel Verweis in Wert Argument nicht unterstützt | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572336"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Zirkelverweis in Wertargument nicht unterstützt
Es wurde versucht, `JSON.stringify` mit einem ungültigen Wert aufzurufen. Das `value`-Argument, ein Array oder ein Objekt, enthält einen Zirkel Verweis.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie den Zirkel Verweis aus dem Argument.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `john` einen Verweis auf `mary` und `mary` über einen Verweis auf `john`verfügt. um den Zirkel Verweis zu entfernen, entfernen Sie entweder die Eigenschaft `brother` aus dem `mary` Objekt oder die Eigenschaft `sister` aus dem `john` Objekt, oder entfernen Sie Sie.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.](../../javascript/reference/json-parse-function-javascript.md) Analyse-Funktion   
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)