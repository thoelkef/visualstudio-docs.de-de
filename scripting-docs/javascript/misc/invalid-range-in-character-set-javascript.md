---
title: "Ungültiger Bereich im Zeichensatz festlegen (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d0d5ddf282c6994c572668136e6d7283794f6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="invalid-range-in-character-set-javascript"></a>Ungültiger Bereich im Zeichensatz (JavaScript)
Sie haben versucht, einen regulären Ausdruck mit einem ungültigen Zeichen Set-Adressbereich zu erstellen. Zeichensätze müssen zwischen einzelnen Zeichen, z. B. a-Z oder 0-9 liegen; Sie können keine Zeichenklassen z. B. \w in einem Zeichensatz verwenden. Das erste Zeichen im Bereich muss auch vor das zweite Zeichen im Bereich liegen. Zum Beispiel:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden Sie nur einzelne Zeichen, um Ihre reguläre Zeichensatz verfassen, und stellen Sie sicher, dass sie in der richtigen Reihenfolge sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)