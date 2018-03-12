---
title: Erwartete &#39; Catch &#39; | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>Erwartete &#39; Catch &#39;
Sie verwendet die Ausnahmebehandlung **versuchen** blockieren, aber hat nicht die zugeordnete geschrieben **catch** Anweisung. Der Ausnahmebehandlungsmechanismus erfordert, dass der Code die Indizierung fehlschlagen darf zusammen mit dem Code, der nicht ausgeführt werden soll, wenn eine Ausnahme auftritt, in eingebunden werden eine **versuchen** Block. Ausnahmen werden ausgelöst, innerhalb der **versuchen** mit blockiert die **auslösen** -Anweisung und abgefangene außerhalb der **versuchen** Block mit einem oder mehreren **catch**Anweisungen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie die zugeordnete **catch** Block.  
  
-   Versuchen Sie es mit einem **schließlich** anstelle von Sperren einer **catch** Block.  
  
## <a name="see-also"></a>Siehe auch  
 [try … try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)