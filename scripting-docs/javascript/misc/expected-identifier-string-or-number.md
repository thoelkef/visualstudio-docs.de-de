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
ms.openlocfilehash: 06ad8497bfc561a5222eef6975a7336f4599c59d
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861904"
---
# <a name="expected-identifier-string-or-number"></a>Es wurde ein Bezeichner, eine Zeichenfolge oder eine Zahl erwartet
Sie haben falsche Literalsyntax zum Deklarieren eines Objektliterals verwendet. Die Eigenschaften eines Objektliterals müssen ein Bezeichner, eine Zeichenfolge oder eine Zahl sein. Ein Objektliteral (auch als "Objektinitialisierer" bezeichnet) besteht aus einer durch Trennzeichen getrennten Liste von Eigenschaft-Wert-Paaren, die alle in eckige Klammern eingeschlossen sind. Beispiel:  
  
```JavaScript  
var point = {x:1.2, y:-3.4};  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass Sie die richtige Literalsyntax verwenden  
  
## <a name="see-also"></a>Weitere Informationen  
 [Komma Operator (,)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Comma_Operatorhttps://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Comma_Operator)