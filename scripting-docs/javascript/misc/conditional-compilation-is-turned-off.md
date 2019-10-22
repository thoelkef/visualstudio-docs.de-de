---
title: Bedingte Kompilierung ist deaktiviert | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572941"
---
# <a name="conditional-compilation-is-turned-off"></a>Die bedingte Kompilierung ist deaktiviert
Sie haben versucht, eine bedingte Kompilierungs Variable zu verwenden, ohne zuerst die bedingte Kompilierung zu aktivieren. Durch das Aktivieren der bedingten Kompilierung wird der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Compiler aufgefordert, Bezeichner mit @ als bedingte Kompilierungs Variablen zu interpretieren. Zu diesem Zweck beginnen Sie mit dem bedingten Code mit der-Anweisung:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie am Anfang des bedingten Codes die folgende Anweisung hinzu:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)    
 [Variablen für bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)    
 [@cc_on-Anweisung](../../javascript/reference/at-cc-on-statement-javascript.md)    
 [@if-Anweisung](../../javascript/reference/at-if-statement-javascript.md)    
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)