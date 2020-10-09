---
title: "\"Default\" darf in einer Switch-Anweisung nur einmal vorkommen | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862791"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>"default" darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, die **default** -Anweisung mehrmals in einer Switch-Anweisung zu verwenden. Der Standardfall ist immer die letzte Case-Anweisung in einer Switch-Anweisung (der FallThrough-Fall).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie alle zusätzlichen **default** Case-Anweisungen aus der- `switch` Anweisung (verwenden Sie höchstens eine Standard Case-Anweisung in der Switch-Anweisung).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Switch-Anweisung](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Steuern des Programmablaufs](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Reservierte Wörter in JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)