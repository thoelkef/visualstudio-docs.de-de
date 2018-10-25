---
title: Ungültiger Bereich im Zeichensatz festlegen (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903633"
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