---
title: Ausnahme ausgelöst und nicht abgefangen. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349035"
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