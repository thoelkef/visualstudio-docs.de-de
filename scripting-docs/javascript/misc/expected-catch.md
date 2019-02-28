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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841447"
---
# <a name="expected-catch"></a>"catch" erwartet
Sie verwendet die Ausnahmebehandlung **versuchen** blockieren, aber hat nicht die zugeordnete geschrieben **catch** Anweisung. Der Mechanismus zur Ausnahmebehandlung erfordert, dass der Code, der zusammen mit dem Code fehlschlägt, kann, die nicht ausgeführt werden soll, wenn eine Ausnahme auftritt, umschlossen werden, in eine **versuchen** Block. Ausnahmen werden ausgelöst, innerhalb der **versuchen Sie es** mit blockiert die **auslösen** -Anweisung und abgefangene außerhalb der **versuchen Sie es** Block mit einer oder mehreren **catch**Anweisungen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Hinzufügen der zugeordneten **catch** Block.  
  
-   Versuchen Sie es mit einem **schließlich** anstelle von Sperren ein **catch** Block.  
  
## <a name="see-also"></a>Siehe auch  
 [try-try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)