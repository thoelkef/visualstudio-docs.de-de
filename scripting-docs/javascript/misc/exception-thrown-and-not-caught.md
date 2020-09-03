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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814589"
---
# <a name="exception-thrown-and-not-caught"></a>Ausnahme ausgelöst und nicht abgefangen
Sie haben eine- `throw` Anweisung in Ihren Code eingefügt, aber Sie wurde nicht in einen **try** -Block eingeschlossen, oder es war kein zugeordneter **catch** -Block zum Abfangen des Fehlers vorhanden. Ausnahmen werden im **try** -Block mithilfe der **throw** -Anweisung ausgelöst und außerhalb des **try** -Blocks mit einer **catch** -Anweisung abgefangen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Schließen Sie Code ein, der eine Ausnahme in einem **try** -Block auslösen kann, und stellen Sie sicher, dass ein entsprechender **catch** -Block vorhanden ist.  
  
- Stellen Sie sicher, dass die Catch-Anweisung die richtige Form der Ausnahme erwartet.  
  
- Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine weitere entsprechende catch-Anweisung vorhanden ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [Throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [Try... catch... Abschließend-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)