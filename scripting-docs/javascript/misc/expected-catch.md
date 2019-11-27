---
title: "\"Catch\" erwartet | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573427"
---
# <a name="expected-catch"></a>"catch" erwartet
Sie haben den **try** -Block für die Ausnahmebehandlung verwendet, aber die zugehörige **catch** -Anweisung nicht geschrieben. Der Mechanismus für die Ausnahmebehandlung erfordert, dass der Code, der möglicherweise fehlschlägt, zusammen mit dem Code, der nicht ausgeführt werden soll, wenn eine Ausnahme auftritt, in einem **try** -Block umschließt. Ausnahmen werden im **try** -Block mithilfe der **throw** -Anweisung ausgelöst und außerhalb des **try** -Blocks mit einer oder mehreren **catch** -Anweisungen abgefangen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie den zugehörigen **catch** -Block hinzu.  
  
- Versuchen Sie, anstelle eines **catch** -Blocks einen **abschließend** -Block zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [try... catch... letzte Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)