---
title: Bedingter Kompilierung ist deaktiviert. | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-is-turned-off"></a>Die bedingte Kompilierung ist deaktiviert
Sie haben versucht, verwenden Sie eine bedingte Kompilierungsvariable ohne erste eingeräumt bedingte Kompilierung auf. Bedingte Kompilierung einschalten teilt die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Compiler, Interpretieren von Bezeichnern, die als Variablen für die bedingte Kompilierung mit @ beginnt. Dazu müssen Sie den bedingten Code mit der Anweisung ab:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie die folgende Anweisung am Anfang des bedingten Code ein:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onAnweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifAnweisung](../../javascript/reference/at-if-statement-javascript.md)   
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)