---
title: Zirkel Verweis in Wert Argument nicht unterstützt | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817618"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Zirkelverweis in Wertargument nicht unterstützt
Es wurde versucht, mit einem ungültigen Wert aufzurufen `JSON.stringify` . Das `value` Argument, ein Array oder ein Objekt, enthält einen Zirkel Verweis.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie den Zirkel Verweis aus dem Argument.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, weil `john` einen Verweis auf `mary` und `mary` einen Verweis auf enthält `john` . um den Zirkel Verweis zu entfernen, entfernen Sie entweder die-Eigenschaft `brother` aus dem- `mary` Objekt oder die- `sister` Eigenschaft aus dem- `john` Objekt.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON. Analyse-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)