---
title: Erwartete &#39; @&#39; | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633070"
---
# <a name="expected-3939"></a>Erwartete &#39; @&#39;
Sie haben versucht, erstellen Sie eine Variable mit mit bedingten kompilierungsanweisungen verwendet werden soll die `@set` -Anweisung, aber nicht platziert werden, ein at-Zeichen "**@**" vor dem Variablennamen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Hinzufügen einer at-Zeichen "**@**" unmittelbar vor dem Variablennamen. Zum Beispiel:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [@setAnweisung](../../javascript/reference/at-set-statement-javascript.md)   
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)