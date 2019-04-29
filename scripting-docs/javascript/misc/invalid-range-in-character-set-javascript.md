---
title: Ungültiger Bereich im Zeichensatz festlegen (JavaScript) | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 1cbfa4de401c2a1dc0626f8f00dbb0bd1bf24408
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007047"
---
# <a name="invalid-range-in-character-set-javascript"></a>Ungültiger Bereich im Zeichensatz (JavaScript)
Sie haben versucht, die einen regulären Ausdruck mit einem ungültigen Zeichen Set-Adressbereich zu erstellen. Zeichensätze müssen zwischen einzelnen Zeichen, z. B. a-Z oder 0-9 liegen; Zeichenklassen in regulären Ausdrücken wie z. B. \w können nicht in einem Zeichensatz einbezogen werden. Das erste Zeichen im Bereich muss auch vor dem zweiten Zeichen im Bereich stammen. Zum Beispiel:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Verwenden Sie nur einzelne Zeichen, Verfassen Sie Ihre reguläre-Zeichensatz ausgewählt werden, und stellen Sie sicher, dass sie in der richtigen Reihenfolge sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)