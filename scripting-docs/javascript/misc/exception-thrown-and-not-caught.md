---
title: Ausnahme ausgelöst und nicht abgefangen | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862764"
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie haben eine- `throw` Anweisung in Ihren Code eingefügt, aber Sie wurde nicht in einen **try** -Block eingeschlossen, oder es war kein zugeordneter **catch** -Block zum Abfangen des Fehlers vorhanden. Ausnahmen werden im **try** -Block mithilfe der **throw** -Anweisung ausgelöst und außerhalb des **try** -Blocks mit einer **catch** -Anweisung abgefangen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Schließen Sie Code ein, der eine Ausnahme in einem **try** -Block auslösen kann, und stellen Sie sicher, dass ein entsprechender **catch** -Block vorhanden ist.  
  
- Stellen Sie sicher, dass die Catch-Anweisung die richtige Form der Ausnahme erwartet.  
  
- Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine weitere entsprechende catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Error-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Throw-Anweisung](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [Try... catch... Abschließend-Anweisung](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)