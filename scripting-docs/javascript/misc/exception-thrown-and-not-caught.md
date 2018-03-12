---
title: "Die Ausnahme ausgelöst und nicht abgefangen | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie enthalten eine `throw` Anweisung im Code, aber es wurde keine eingefasst eine **versuchen** blockieren, oder es wurde keine zugeordnete **catch** Block, um den Fehler. Ausnahmen werden ausgelöst, innerhalb der **versuchen Sie es** mit blockiert die **auslösen** -Anweisung und abgefangene außerhalb der **versuchen Sie es** -block mit einer **catch** -Anweisung.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Schließen Sie Code, der eine Ausnahme, in auslösen kann eine **versuchen** blockieren, und Sie sicher, dass es ein entsprechendes **catch** Block.  
  
-   Stellen Sie sicher, dass die Catch-Anweisung erwartet, dass die richtige Art der Ausnahme.  
  
-   Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine andere entsprechende Catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)