---
title: Bedingte Kompilierung ist deaktiviert | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816123"
---
# <a name="conditional-compilation-is-turned-off"></a>Die bedingte Kompilierung ist deaktiviert
Sie haben versucht, eine bedingte Kompilierungs Variable zu verwenden, ohne zuerst die bedingte Kompilierung zu aktivieren. Das Aktivieren der bedingten Kompilierung weist den [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Compiler an, Bezeichner zu interpretieren, die mit @ als bedingte Kompilierungs Variablen beginnen. Zu diesem Zweck beginnen Sie mit dem bedingten Code mit der-Anweisung:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie am Anfang des bedingten Codes die folgende Anweisung hinzu:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on An](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if An](../../javascript/reference/at-if-statement-javascript.md)   
 [@set An](../../javascript/reference/at-set-statement-javascript.md)