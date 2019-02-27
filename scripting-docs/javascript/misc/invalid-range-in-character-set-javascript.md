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
ms.openlocfilehash: 6b1e404a9df368f639530d533b8cf4bf063f8ad6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842428"
---
# <a name="invalid-range-in-character-set-javascript"></a>Ungültiger Bereich im Zeichensatz (JavaScript)
Sie haben versucht, die einen regulären Ausdruck mit einem ungültigen Zeichen Set-Adressbereich zu erstellen. Zeichensätze müssen zwischen einzelnen Zeichen, z. B. a-Z oder 0-9 liegen; Zeichenklassen in regulären Ausdrücken wie z. B. \w können nicht in einem Zeichensatz einbezogen werden. Das erste Zeichen im Bereich muss auch vor dem zweiten Zeichen im Bereich stammen. Zum Beispiel:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden Sie nur einzelne Zeichen, Verfassen Sie Ihre reguläre-Zeichensatz ausgewählt werden, und stellen Sie sicher, dass sie in der richtigen Reihenfolge sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)