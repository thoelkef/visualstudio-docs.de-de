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
ms.openlocfilehash: e1e34be9f8eab5171af0e2553d5777b0958bf3c2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840869"
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie enthalten eine `throw` -Anweisung in Ihrem Code, aber es wurde keine eingefasst eine **versuchen** -Block, oder es wurde keine zugeordnete **catch** Block zum Abfangen des Fehlers. Ausnahmen werden ausgelöst, innerhalb der **versuchen Sie es** mit blockiert die **auslösen** -Anweisung und abgefangene außerhalb der **versuchen Sie es** -block mit einer **catch** -Anweisung.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Einschließen von Code, der eine Ausnahme, in auslösen kann eine **versuchen** blockieren, und stellen Sie sicher, es wird eine entsprechende **catch** Block.  
  
-   Stellen Sie sicher, dass die Catch-Anweisung erwartet, dass die richtige Art der Ausnahme.  
  
-   Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine andere entsprechende Catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [Throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)