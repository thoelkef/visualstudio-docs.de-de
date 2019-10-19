---
title: Ausnahme ausgelöst und nicht abgefangen | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572856"
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie haben eine `throw`-Anweisung in Ihren Code eingefügt, aber Sie wurde nicht in einen **try** -Block eingeschlossen, oder es war kein zugeordneter **catch** -Block zum Abfangen des Fehlers vorhanden. Ausnahmen werden im **try** -Block mithilfe der **throw** -Anweisung ausgelöst und außerhalb des **try** -Blocks mit einer **catch** -Anweisung abgefangen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Schließen Sie Code ein, der eine Ausnahme in einem **try** -Block auslösen kann, und stellen Sie sicher, dass ein entsprechender **catch** -Block vorhanden ist.  
  
- Stellen Sie sicher, dass die Catch-Anweisung die richtige Form der Ausnahme erwartet.  
  
- Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine weitere entsprechende catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler Objekt](../../javascript/reference/error-object-javascript.md)    
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)    
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)