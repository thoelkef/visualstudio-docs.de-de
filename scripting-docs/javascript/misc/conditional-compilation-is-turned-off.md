---
title: "Die bedingte Kompilierung ist deaktiviert | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Die bedingte Kompilierung ist deaktiviert
Sie haben versucht, eine Variable für die bedingten Kompilierung zu verwenden, ohne die bedingte Kompilierung zuerst aktiviert zu haben.  Durch die Aktivierung der bedingten Kompilierung wird der [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Compiler angewiesen, die Bezeichner, die mit @ beginnen, als Variablen für die bedingte Kompilierung zu interpretieren.  Hierzu beginnen Sie den Bedingungscode mit folgender Anweisung:  
  
```  
/*@cc_on @*/  
```  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie am Anfang der Codedatei die folgende Anweisung ein:  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on\-Anweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if\-Anweisung](../../javascript/reference/at-if-statement-javascript.md)   
 [@set\-Anweisung](../../javascript/reference/at-set-statement-javascript.md)