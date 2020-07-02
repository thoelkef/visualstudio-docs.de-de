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
ms.openlocfilehash: a81634a96fb85584c9176db8c72bfc5c3468dc2c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816877"
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
 [Reguläres Ausdrucks Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)