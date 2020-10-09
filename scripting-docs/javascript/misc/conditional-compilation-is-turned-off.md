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
ms.openlocfilehash: 91e32971013d2dfcf0ee2dc901d84681522c7e89
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861650"
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
 [Bedingte Kompilierung](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variablen für bedingte Kompilierung](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on An](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if An](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set An](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)