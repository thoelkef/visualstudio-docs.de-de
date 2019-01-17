---
title: Für die bedingte Kompilierung ist deaktiviert. | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347345"
---
# <a name="conditional-compilation-is-turned-off"></a>Die bedingte Kompilierung ist deaktiviert
Sie haben versucht, die auf eine Variable für die bedingte Kompilierung, ohne zuerst aktivieren, für die bedingte Kompilierung verwenden. Aktivieren der für die bedingte Kompilierung weist die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Compiler interpretiert Bezeichner als bedingte Kompilierungsvariablen mit @ beginnt. Dazu müssen Sie den bedingten Code mit der Anweisung ab:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie die folgende Anweisung am Anfang des bedingten Code aus:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Anweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Anweisung](../../javascript/reference/at-if-statement-javascript.md)   
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)