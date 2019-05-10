---
title: Ausnahme ausgelöst und nicht abgefangen. | Microsoft-Dokumentation
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
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946328"
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie enthalten eine `throw` -Anweisung in Ihrem Code, aber es wurde keine eingefasst eine **versuchen** -Block, oder es wurde keine zugeordnete **catch** Block zum Abfangen des Fehlers. Ausnahmen werden ausgelöst, innerhalb der **versuchen Sie es** mit blockiert die **auslösen** -Anweisung und abgefangene außerhalb der **versuchen Sie es** -block mit einer **catch** -Anweisung.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Einschließen von Code, der eine Ausnahme, in auslösen kann eine **versuchen** blockieren, und stellen Sie sicher, es wird eine entsprechende **catch** Block.  
  
- Stellen Sie sicher, dass die Catch-Anweisung erwartet, dass die richtige Art der Ausnahme.  
  
- Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine andere entsprechende Catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [Throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)