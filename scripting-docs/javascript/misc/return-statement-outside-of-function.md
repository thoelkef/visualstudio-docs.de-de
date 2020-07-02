---
title: Return-Anweisung außerhalb der Funktion | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32eadcf5ae88dbe64c8ccdb3effbb85bc79f9b32
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816734"
---
# <a name="return-statement-outside-of-function"></a>return-Anweisung ist außerhalb der Funktion
Sie haben eine- `return` Anweisung im globalen Gültigkeitsbereich Ihres Codes verwendet. Die- `return` Anweisung sollte nur im Text einer Funktion angezeigt werden.  
  
 Das Aufrufen einer Funktion mit dem- `()` Operator ist ein Ausdruck. Alle Ausdrücke haben Werte. die- `return` Anweisung wird verwendet, um den Wert anzugeben, der von einer Funktion zurückgegeben wird. Die allgemeine Form ist:  
  
```js
  
return [ expression ];  
```  
  
 Wenn die `return` Anweisung ausgeführt wird, wird der *Ausdruck* ausgewertet und als Wert der Funktion zurückgegeben. Wenn kein Ausdruck vorhanden ist, wird "nicht **definiert** " zurückgegeben.  
  
 Die Ausführung der Funktion wird beendet, wenn die `return` Anweisung ausgeführt wird, auch wenn noch andere Anweisungen im Funktions Rumpf verbleiben. Eine Ausnahme von dieser Regel ist, wenn die Return-Anweisung innerhalb eines **try** -Blocks auftritt und ein entsprechender Block "After" vorhanden ist, wird der Code **im Block "** **endlich** " ausgeführt, bevor die Funktion zurück **gegeben** wird.  
  
 Wenn eine Funktion zurückgibt, weil Sie das Ende des Funktions Texts erreicht, ohne dass eine-Anweisung ausgeführt wird `return` , ist der zurückgegebene Wert der nicht **definierte** Wert (Dies bedeutet, dass das Funktionsergebnis nicht als Teil eines größeren Ausdrucks verwendet werden kann).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie die- `return` Anweisung aus dem Hauptteil des Codes (dem globalen Gültigkeitsbereich).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Return-Anweisung](../../javascript/reference/return-statement-javascript.md)   
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [caller-Eigenschaft (Funktion)](../../javascript/reference/caller-property-function-javascript.md)