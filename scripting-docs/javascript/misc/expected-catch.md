---
title: "\"Catch\" erwartet | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816683"
---
# <a name="expected-catch"></a>"catch" erwartet
Sie haben den **try** -Block für die Ausnahmebehandlung verwendet, aber die zugehörige **catch** -Anweisung nicht geschrieben. Der Mechanismus für die Ausnahmebehandlung erfordert, dass der Code, der möglicherweise fehlschlägt, zusammen mit dem Code, der nicht ausgeführt werden soll, wenn eine Ausnahme auftritt, in einem **try** -Block umschließt. Ausnahmen werden im **try** -Block mithilfe der **throw** -Anweisung ausgelöst und außerhalb des **try** -Blocks mit einer oder mehreren **catch** -Anweisungen abgefangen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie den zugehörigen **catch** -Block hinzu.  
  
- Versuchen Sie, anstelle eines **catch** -Blocks einen **abschließend** -Block zu verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Try... catch... Abschließend-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)