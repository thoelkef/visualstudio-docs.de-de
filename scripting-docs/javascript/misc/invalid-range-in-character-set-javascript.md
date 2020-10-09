---
title: Ungültiger Bereich im Zeichensatz (JavaScript) | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12624d1a0256360ef1e4538a14100923c7de8af8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862585"
---
# <a name="invalid-range-in-character-set-javascript"></a>Ungültiger Bereich im Zeichensatz (JavaScript)
Sie haben versucht, einen regulären Ausdruck mit einem ungültigen Zeichensatz Bereich zu erstellen. Zeichensätze müssen nur aus einzelnen Zeichen bestehen, z. b. a-z oder 0-9; Zeichenklassen wie z. b. \w können nicht in einen Zeichensatz eingeschlossen werden. Das erste Zeichen im Bereich muss auch vor dem zweiten Zeichen im Bereich liegen. Beispiel:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Verwenden Sie nur einzelne Zeichen, um den Zeichensatz für reguläre Ausdrücke zu verfassen, und stellen Sie sicher, dass Sie in der richtigen Reihenfolge vorliegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reguläres Ausdrucks Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntax für reguläre Ausdrücke (JavaScript)](/previous-versions/1400241x(v=vs.100))