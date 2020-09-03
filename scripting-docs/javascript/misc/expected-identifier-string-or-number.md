---
title: Bezeichner, Zeichenfolge oder Zahl erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1028
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f6bb8398-4fd6-4312-b4be-9617a2834cc4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c0e1ee1cdb2c135d3a76316d56e279de963b156
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814576"
---
# <a name="expected-identifier-string-or-number"></a>Es wurde ein Bezeichner, eine Zeichenfolge oder eine Zahl erwartet
Sie haben falsche Literalsyntax zum Deklarieren eines Objektliterals verwendet. Die Eigenschaften eines Objektliterals müssen ein Bezeichner, eine Zeichenfolge oder eine Zahl sein. Ein Objektliteral (auch als "Objektinitialisierer" bezeichnet) besteht aus einer durch Trennzeichen getrennten Liste von Eigenschaft-Wert-Paaren, die alle in eckige Klammern eingeschlossen sind. Beispiel:  
  
```JavaScript  
var point = {x:1.2, y:-3.4};  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass Sie die richtige Literalsyntax verwenden  
  
## <a name="see-also"></a>Weitere Informationen  
 [Komma Operator (,)](../../javascript/reference/comma-operator-decrement-javascript.md)